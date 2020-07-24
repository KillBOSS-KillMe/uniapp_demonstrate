<template>
	<view>
		<page-head title="checkbox"></page-head>
		<label-description :title="labelDescription"></label-description>
		<view class="paddingWrap">
			<view class="title">默认样式</view>
			<view>
				<checkbox-group>
					<label>
						<checkbox value="cb" checked="true" />
						选中
					</label>
					<label>
						<checkbox value="cb" />
						未选中
					</label>
				</checkbox-group>
			</view>
			<view class="title">不同颜色和尺寸的checkbox</view>
			<view>
				<checkbox-group>
					<label>
						<checkbox value="cb" checked="true" color="#FFCC33" style="transform:scale(0.7)" />
						选中
					</label>
					<label>
						<checkbox value="cb" color="#FFCC33" style="transform:scale(0.7)" />
						未选中
					</label>
				</checkbox-group>
			</view>
		</view>

		<view class="paddingWrap">
			<view class="title">
				推荐展示样式
				<text>使用 uni-list 布局</text>
			</view>
		</view>
		<view class="paddingWrap">
			<checkbox-group @change="checkboxChange">
				<label class="uni-list-cell uni-list-cell-pd" v-for="item in items" :key="item.value">
					<view><checkbox :value="item.value" :checked="item.checked" /></view>
					<view>{{ item.name }}</view>
				</label>
			</checkbox-group>
		</view>
	</view>
</template>
<script>
export default {
	data() {
		return {
			labelDescription: 'checkbox 复选框',
			title: 'checkbox 复选框',
			items: [
				{
					value: 'USA',
					name: '美国'
				},
				{
					value: 'CHN',
					name: '中国',
					checked: 'true'
				},
				{
					value: 'BRA',
					name: '巴西'
				},
				{
					value: 'JPN',
					name: '日本'
				},
				{
					value: 'ENG',
					name: '英国'
				},
				{
					value: 'FRA',
					name: '法国'
				}
			]
		};
	},
	methods: {
		checkboxChange: function(e) {
			var items = this.items,
				values = e.detail.value;
			for (var i = 0, lenI = items.length; i < lenI; ++i) {
				const item = items[i];
				if (values.includes(item.value)) {
					this.$set(item, 'checked', true);
				} else {
					this.$set(item, 'checked', false);
				}
			}
		}
	}
};
</script>

<style lang="scss">
.paddingWrap {
	width: 690rpx;
	padding: 0 30rpx;
	.title {
		margin: 30rpx 0;
		font-size: $titleSize_1;
		color: $mainFontColor;
		font-weight: $mainFontWeight;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	label {
		display: flex;
		align-items: center;
		justify-content: flex-start;
		padding: 30rpx 0;
		border-bottom: 1rpx solid $borderColor;
	}
}
.uni-list-cell {
	justify-content: flex-start;
}
</style>
