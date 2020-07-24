<template>
	<view>
		<page-head title="view"></page-head>
		<label-description :title="labelDescription"></label-description>
		<view class="paddingWrap">
			<view class="title">
				flex-direction: row
				<text>\n横向布局</text>
			</view>
			<view class="flexRow">
				<view class="colorView BGred">A</view>
				<view class="colorView BGgreen">B</view>
				<view class="colorView BGblue">C</view>
			</view>

			<view class="title">
				flex-direction: column
				<text>\n纵向布局</text>
			</view>
			<view class="flexColumn">
				<view class="colorView BGred">A</view>
				<view class="colorView BGgreen">B</view>
				<view class="colorView BGblue">C</view>
			</view>

			<view class="title">
				更多布局示例
				<text>\nflex布局演示</text>
			</view>
			<view>
				<view class="text">纵向布局-自动宽度</view>
				<view class="text" style="width: 300rpx;">纵向布局-固定宽度</view>
				<view class="flexRow">
					<view class="text">横向布局-自动宽度</view>
					<view class="text">横向布局-自动宽度</view>
				</view>
				<view class="flexRow" style="-webkit-justify-content: center;justify-content: center;">
					<view class="text">横向布局-居中</view>
					<view class="text">横向布局-居中</view>
				</view>
				<view class="flexRow" style="-webkit-justify-content: flex-end;justify-content: flex-end;">
					<view class="text">横向布局-居右</view>
					<view class="text">横向布局-居右</view>
				</view>
				<view class="uni-flex uni-row">
					<view class="text" style="-webkit-flex: 1;flex: 1;">横向布局-平均分布</view>
					<view class="text" style="-webkit-flex: 1;flex: 1;">横向布局-平均分布</view>
				</view>
				<view class="flexRow" style="-webkit-justify-content: space-between;justify-content: space-between;">
					<view class="text">横向布局-两端对齐</view>
					<view class="text">横向布局-两端对齐</view>
				</view>
				<view class="flexRow">
					<view class="text" style="width: 200rpx;">固定宽度</view>
					<view class="text" style="-webkit-flex: 1;flex: 1;">自动占满余量</view>
				</view>
				<view class="flexRow">
					<view class="text" style="width: 200rpx;">固定宽度</view>
					<view class="text" style="-webkit-flex: 1;flex: 1;">自动占满</view>
					<view class="text" style="width: 200rpx;">固定宽度</view>
				</view>
				<view class="flexRow" style="-webkit-flex-wrap: wrap;flex-wrap: wrap;">
					<view class="text" style="width: 280rpx;">一行显示不全,wrap折行</view>
					<view class="text" style="width: 280rpx;">一行显示不全,wrap折行</view>
					<view class="text" style="width: 280rpx;">一行显示不全,wrap折行</view>
				</view>
				<view class="flexColumn">
					<view class="text uni-flex" style="align-items: center;-webkit-flex: 1;display: flex;height: 200rpx;-webkit-justify-content: center;justify-content: center;-webkit-align-items: flex-start;align-items: flex-start;">
						<text>垂直居顶</text>
					</view>
					<view class="text uni-flex" style="align-items: center;-webkit-flex: 1;display: flex;height: 200rpx;-webkit-justify-content: center;justify-content: center;-webkit-align-items: center;align-items: center;">
						<text>垂直居中</text>
					</view>
					<view class="text uni-flex" style="align-items: center;-webkit-flex: 1;display: flex;height: 200rpx;-webkit-justify-content: center;justify-content: center;-webkit-align-items: flex-end;align-items: flex-end;">
						<text>垂直居底</text>
					</view>
				</view>
			</view>

			<view class="title">
				组合示例
				<text>\nflex布局演示</text>
			</view>
			<view class="flexRow">
				<view class="text uni-flex" style="width: 200rpx;height: 220rpx;-webkit-justify-content: center;justify-content: center;-webkit-align-items: center;align-items: center;">
					<!-- <image src="../../../static/plus.png" style="width: 150rpx;height: 150rpx;"></image> -->
				</view>
				<view class="uni-flex uni-column" style="-webkit-flex: 1;flex: 1;-webkit-justify-content: space-between;justify-content: space-between;">
					<view class="text" style="height: 120rpx;text-align: left;padding-left: 20rpx;padding-top: 10rpx;">
						文字居左，留出左间距
					</view>
					<view class="uni-flex uni-row">
						<view class="text" style="-webkit-flex: 1;flex: 1;">剩余数量</view>
						<view class="text" style="-webkit-flex: 1;flex: 1;">立即购买</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				labelDescription: "Flex是Flexible Box的缩写，意为“弹性布局”，用来为盒状模型提供最大的灵活性。当设置display: flex后，继续给view等容器组件设置flex-direction:row或column，就可以在该容器内按行或列排布子组件。uni-app推荐使用flex布局。因为flex布局有利于跨更多平台，尤其是采用原生渲染的平台。"
			}
		}
	}
</script>

<style lang="scss">
	.paddingWrap{
		width:690rpx;
		padding:0 30rpx;
		.title {
			font-size: $titleSize_1;
			color: $mainFontColor;
			text {
				padding: 10rpx;
				color: $FontColor;
			}
		}
		.flexRow {
			margin: 20rpx 0;
			display: flex;
			flex-direction: row;
			.colorView {
				width: 33.3%;
				height: 200rpx;
				text-align: center;
				line-height: 200rpx;
			}
		}
		.flexColumn {
			margin: 20rpx 0;
			display: flex;
			flex-direction: column;
			.colorView {
				width: 100%;
				height: 200rpx;
				text-align: center;
				line-height: 200rpx;
			}
		}
	}
	.flex-item {
		width: 33.3%;
		height: 200rpx;
		text-align: center;
		line-height: 200rpx;
	}

	.flex-item-V {
		width: 100%;
		height: 150rpx;
		text-align: center;
		line-height: 150rpx;
	}

	.text {
		margin: 15rpx 10rpx;
		padding: 0 20rpx;
		background-color: #ebebeb;
		height: 70rpx;
		line-height: 70rpx;
		text-align: center;
		color: #777;
		font-size: 26rpx;
	}

	.desc {
		/* text-indent: 40rpx; */
	}
</style>
