<template>
	<view>
		<page-head title="scroll-view"></page-head>
		<label-description :title="labelDescription"></label-description>
		<view class="paddingWrap">
			<view class="title">
				Vertical Scroll
				<text>\n纵向滚动</text>
			</view>
			<scroll-view scroll-y="true" class="scrollRow">
				<view class="colorView BGred">A</view>
				<view class="colorView BGgreen">B</view>
				<view class="colorView BGblue">C</view>
			</scroll-view>

			<view class="title">
				Horizontal Scroll
				<text>\n横向滚动</text>
			</view>
			<scroll-view scroll-x class="scrollColumn">
				<view class="colorView BGred">A</view>
				<view class="colorView BGgreen">B</view>
				<view class="colorView BGblue">C</view>
			</scroll-view>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				labelDescription: "区域滚动视图"
			}
		}
	}
</script>

<style lang="scss">
	.paddingWrap{
		width:690rpx;
		height: auto;
		padding:0 30rpx;
		.title {
			font-size: $titleSize_1;
			color: $mainFontColor;
			text {
				padding: 10rpx;
				color: $FontColor;
			}
		}
		.scrollRow {
			margin: 20rpx 0;
			width: 690rpx;
			height: 200rpx;
			.colorView {
				width: 100%;
				height: 200rpx;
				text-align: center;
				line-height: 200rpx;
			}
		}
		.scrollColumn {
			margin: 20rpx 0;
			width: 690rpx;
			height: 200rpx;
			white-space: nowrap;
			overflow:hidden;
			.colorView {
				display: inline-block;
				width: 690rpx;
				height: 200rpx;
				text-align: center;
				line-height: 200rpx;
			}
		}
	}
</style>
