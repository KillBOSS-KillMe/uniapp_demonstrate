<template name="page-head">
	<view class="pageHead">
		<view class="pageName">{{title}}</view>
	</view>
</template>
<script>
	export default {
		name: "page-head",
		props: {
			title: {
				type: String,
				default: ""
			}
		}
	}
</script>
<style lang="scss">
	.pageHead {
		width: 100vw;
		height: auto;
		padding: 30rpx 0;
		display: flex;
		align-items: center;
		justify-content: center;
		.pageName {
			width: auto;
			height: auto;
			padding: 10rpx;
			font-size: 50rpx;
			color: $mainFontColor;
			font-weight: $fontColor_2;
			border-bottom: 1rpx solid #eee;
		}
	}
</style>