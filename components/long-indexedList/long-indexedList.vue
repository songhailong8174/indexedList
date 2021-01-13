<template>
	<view class="long-indexedList">
		<view class="left">
			<scroll-view 
				scroll-y
				scroll-with-animation
				:style="`height:${ height }px`"
				@scroll="scroll"
				:scroll-into-view="cIndex"
				@scrolltolower="scrollToBottom"
			>
				<view v-for="(item, index) in list" :key="index">
					<view class="item-label" :id="`cid${ index }`">{{ item.label }}</view>
					<view class="list-container">
						<view
							v-for="(child, cIndex) in item.children"
							:key="cIndex"
							class="list-item"
							:class="{'active': selectedMap[child.id] != undefined }"
							@click="itemClick(child)"
						>
							{{ child.label }}
						</view>
					</view>
				</view>
			</scroll-view>
		</view>
		<view class="right">
			<scroll-view 
				scroll-y
				:style="`height:${ height }px`"
				scroll-with-animation
			>
				<view 
					class="index-words"
					:class="{ 'index-words-active': index === activeIndex }"
					v-for="(item, index) in list" 
					:key="item.label"
					@click="indexedClick(index)"
				>
					{{ item.label }}
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			list: {
				type: Array,
				default: () => []
			},
			multi: {
				type: Boolean,
				default: false
			}
		},
		data() {
			return {
				activeIndex: 0,
				height: 0,
				cIndex: '',
				topList: [],
				flag: false,
				selectedMap: {}
			};
		},
		methods: {
			indexedClick (index) {
				this.$nextTick(() => {
					this.cIndex = `cid${ index }`
					this.flag = true
				})
				this.cIndex = ''
				this.activeIndex = index
			},
			itemClick (item) {
				if (!this.multi) {
					Object.keys(this.selectedMap).forEach(key => {
						this.$delete(this.selectedMap, key)
					})
				}
				if (this.selectedMap[item.id] != undefined) {
					this.$delete(this.selectedMap, item.id)
				} else {
					this.$set(this.selectedMap, item.id, item)
				}
				this.$emit('change', this.getValues())
			},
			scroll(e) {
				if(this.flag){
					this.flag = false
					return
				}
				let scrollTop = e.target.scrollTop
				for(let i = 0;i < this.topList.length; i++){
					let h1 = this.topList[i]
					let h2 = this.topList[i + 1]
					if(scrollTop > h1 && scrollTop < h2) {
						this.activeIndex = i
					}
				}
			},
			getNodesInfo () {
				const query = uni.createSelectorQuery().in(this);
				query.selectAll('.item-label').boundingClientRect().exec(res=>{
					let nodes = res[0]
					this.topList =  nodes.map(item => item.top)
				})
			},
			scrollToBottom () {
				// setTimeout(()=>{
				// 	this.activeIndex = this.list.length - 1
				// }, 50)
			},
			getValues () {
				return Object.values(JSON.parse(JSON.stringify(this.selectedMap)))
			}
		},
		mounted() {
			uni.getSystemInfo({
				success: res => {
					this.height = res.screenHeight;
				}
			})
			this.getNodesInfo()
		}
	}
</script>

<style lang="scss" scoped>
	.long-indexedList {
		display: flex;
		justify-content: space-between;
		color: #333333;
		.left {
			width: 76%;
			padding-left: 46upx;
			.item-label {
				padding: 0 0 24upx 6upx;
			}
			.list-container {
				display: flex;
				justify-content: space-between;
				.list-item {
					width: 154upx;
					height: 68upx;
					margin-bottom: 36upx;
					line-height: 68upx;
					border: solid #CCCCCC 2upx;
					border-radius: 24upx;
					text-align: center;
					background: #FFFFFF;
				}
				.active {
					background: #FFF7EE;
					border: 2upx solid #FFE4C6;
					color: #F8571A;
				}
			}
		}
		.right {
			margin-right: 36upx;
			padding-top: 148upx;
			.index-words {
				margin-bottom: 16upx;
				width: 60upx;
				height: 60upx;
				line-height: 60upx;
				text-align: center;
			}
			.index-words-active {
				background: #6F61DA;
				color: #FFFFFF;
				border-radius: 50%;
			}
		}
	}
</style>
