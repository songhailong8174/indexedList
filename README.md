## indexedList索引列表

uni-app索引列表，用于城市选择、分类选择等。

> Github地址：https://github.com/songhailong8174/indexedList

## 组件使用方式

将 **long-indexedList** 复制到 uni-app项目中的 **components**目录即可

```vue
<template>
	<view>
		<long-indexedList
			:list="list"
			@change="change"
		>
		</long-indexedList>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: []
			}
		},
		onLoad() {
			this.init()
		},
		methods: {
			init () {
				this.list = [
					{ label: 'A', children: [ { id: 'A01', label: 'A01' }, { id: 'A02', label: 'A02' }, { id: 'A03', label: 'A03' } ] },
					{ label: 'B', children: [ { id: 'B01', label: 'B01' }, { id: 'B02', label: 'B02' }, { id: 'B03', label: 'B03' } ] },
					{ label: 'C', children: [ { id: 'C01', label: 'C01' }, { id: 'C02', label: 'C02' }, { id: 'C03', label: 'C03' } ] },
					{ label: 'D', children: [ { id: 'D01', label: 'D01' }, { id: 'D02', label: 'D02' }, { id: 'D03', label: 'D03' } ] },
					{ label: 'E', children: [ { id: 'E01', label: 'E01' }, { id: 'E02', label: 'E02' }, { id: 'E03', label: 'E03' } ] },
					{ label: 'F', children: [ { id: 'F01', label: 'F01' }, { id: 'F02', label: 'F02' }, { id: 'F03', label: 'F03' } ] },
					{ label: 'G', children: [ { id: 'G01', label: 'G01' }, { id: 'G02', label: 'G02' }, { id: 'G03', label: 'G03' } ] },
					{ label: 'H', children: [ { id: 'H01', label: 'H01' }, { id: 'H02', label: 'H02' }, { id: 'H03', label: 'H03' } ] },
					{ label: 'I', children: [ { id: 'I01', label: 'I01' }, { id: 'I02', label: 'I02' }, { id: 'I03', label: 'I03' } ] },
					{ label: 'J', children: [ { id: 'J01', label: 'J01' }, { id: 'J02', label: 'J02' }, { id: 'J03', label: 'J03' } ] },
					{ label: 'K', children: [ { id: 'K01', label: 'K01' }, { id: 'K02', label: 'K02' }, { id: 'K03', label: 'K03' } ] },
					{ label: 'L', children: [ { id: 'L01', label: 'L01' }, { id: 'L02', label: 'L02' }, { id: 'L03', label: 'L03' } ] },
					{ label: 'M', children: [ { id: 'M01', label: 'M01' }, { id: 'M02', label: 'M02' }, { id: 'M03', label: 'M03' } ] },
					{ label: 'N', children: [ { id: 'N01', label: 'N01' }, { id: 'N02', label: 'N02' }, { id: 'N03', label: 'N03' } ] },
					{ label: 'O', children: [ { id: 'O01', label: 'O01' }, { id: 'O02', label: 'O02' }, { id: 'O03', label: 'O03' } ] },
					{ label: 'P', children: [ { id: 'P01', label: 'P01' }, { id: 'P02', label: 'P02' }, { id: 'P03', label: 'P03' } ] },
					{ label: 'Q', children: [ { id: 'Q01', label: 'Q01' }, { id: 'Q02', label: 'Q02' }, { id: 'Q03', label: 'Q03' } ] },
					{ label: 'R', children: [ { id: 'R01', label: 'R01' }, { id: 'R02', label: 'R02' }, { id: 'R03', label: 'R03' } ] },
					{ label: 'S', children: [ { id: 'S01', label: 'S01' }, { id: 'S02', label: 'S02' }, { id: 'S03', label: 'S03' } ] },
					{ label: 'T', children: [ { id: 'T01', label: 'T01' }, { id: 'T02', label: 'T02' }, { id: 'T03', label: 'T03' } ] }
				]
			},
			change (data) {
				console.log(data)
			}
		}
	}
</script>
```

## list数据结构

| 名称     | 类型   | 说明                                      |
| -------- | ------ | ----------------------------------------- |
| label    | String | 分组显示名称，可根据需要修改              |
| children | Array  | 分类列表，详细数据结构见 children结构描述 |

### children数据结构

| 名称  | 类型   | 说明                         |
| ----- | ------ | ---------------------------- |
| id    | String | 元素唯一标志                 |
| label | String | 元素显示名称，可根据需要修改 |



## 属性

| 名称  | 类型    | 默认值 | 说明                 |
| ----- | ------- | ------ | -------------------- |
| list  | Array   | []     | 列表数据             |
| multi | Boolean | false  | 是否多选，默认为单选 |

## 事件

| 名称   | 返回值 | 说明               |
| ------ | ------ | ------------------ |
| change | Array  | 返回选中的数据数组 |

## 方法

| 名称        | 说明                                         |
| ----------- | -------------------------------------------- |
| getValues() | 获取选中的数据数组，和change事件中的数据一致 |

## 使用示例

详细代码 [Demo](https://github.com/songhailong8174/indexedList)

## 插件截图

![img](https://cdn.jsdelivr.net/gh/songhailong8174/images/img/indexedList-single.png)


![img](https://cdn.jsdelivr.net/gh/songhailong8174/images/img/indexedList-multi.png)


PS：如有问题可联系QQ（1365763165）或者提issure，如果帮到你了还请不要吝啬给个 [Star](https://github.com/songhailong8174/indexedList)

