<template name="label-description">
	<view class="pageHead">{{title}}</view>
</template>
<script>
	export default {
		name: "label-description",
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
		width: 690rpx;
		height: auto;
		padding: 30rpx;
		font-size: 30rpx;
		color: $mainFontColor;
		line-height: 40rpx;
	}
</style>