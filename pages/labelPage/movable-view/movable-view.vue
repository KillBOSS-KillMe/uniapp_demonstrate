<template>
	<view>
		<page-head title="movable-area"></page-head>
		<label-description :title="labelDescription"></label-description>
		<view class="paddingWrap">
			<view class="listCell">
				<text>示例 1</text>
				<text>movable-view 区域小于 movable-area</text>
			</view>
			<movable-area><movable-view :x="x" :y="y" direction="all" @change="onChange">text</movable-view></movable-area>
			<view @tap="tap" class="uni-link uni-center uni-common-mt">点击这里移动至 (30px, 30px)</view>
			<view class="listCell">
				<text>示例 2</text>
				<text>movable-view区域大于movable-area</text>
			</view>
			<movable-area><movable-view class="max" direction="all">text</movable-view></movable-area>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			x: 0,
			y: 0,
			old: {
				x: 0,
				y: 0
			}
		};
	},
	methods: {
		tap: function(e) {
			this.x = this.old.x;
			this.y = this.old.y;
			this.$nextTick(function() {
				this.x = 30;
				this.y = 30;
			});
		},
		onChange: function(e) {
			this.old.x = e.detail.x;
			this.old.y = e.detail.y;
		}
	}
};
</script>

<style lang="scss">
.paddingWrap {
	width: 690rpx;
	padding: 0 30rpx;
	.listCell {
		width: 100%;
		height: auto;
		padding: 30rpx 0;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	movable-area {
		width: 100%;
		height: 300rpx;
		background: $themeBGColor;
		margin: 30rpx 0;
		overflow: hidden;
		movable-view {
			width: 100rpx;
			height: 100rpx;
			display: flex;
			align-items: center;
			justify-content: center;
			background-color: $themeColor;
			color: #fff;
		}
		.max {
			width: 400rpx;
			height: 400rpx;
		}
	}
}
</style>
