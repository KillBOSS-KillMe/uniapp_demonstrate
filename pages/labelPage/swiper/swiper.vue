<template>
	<view>
		<page-head title="swiper"></page-head>
		<label-description :title="labelDescription"></label-description>
		<view class="paddingWrap">
			<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
				<swiper-item><view class="BGred">A</view></swiper-item>
				<swiper-item><view class="BGgreen">B</view></swiper-item>
				<swiper-item><view class="BGblue">C</view></swiper-item>
			</swiper>
		</view>
		<view class="paddingWrap">
			<view class="listCell">
				<view>指示点</view>
				<switch :checked="indicatorDots" @change="changeIndicatorDots" />
			</view>
			<view class="listCell">
				<view>自动播放</view>
				<switch :checked="autoplay" @change="changeAutoplay" />
			</view>
		</view>
		<view class="paddingWrap">
			<view class="listCell">
				<text>幻灯片切换时长(ms)</text>
				<text class="info">{{ duration }}</text>
			</view>
			<slider @change="durationChange" :value="duration" min="500" max="2000" />
			<view class="listCell">
				<text>自动播放间隔时长(ms)</text>
				<text class="info">{{ interval }}</text>
			</view>
			<slider @change="intervalChange" :value="interval" min="2000" max="10000" />
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			labelDescription: '滑块视图容器,一般用于左右滑动或上下滑动，比如banner轮播图。',
			background: ['color1', 'color2', 'color3'],
			indicatorDots: true,
			autoplay: true,
			interval: 2000,
			duration: 500
		};
	},
	methods: {
		changeIndicatorDots(e) {
			this.indicatorDots = !this.indicatorDots;
		},
		changeAutoplay(e) {
			this.autoplay = !this.autoplay;
		},
		intervalChange(e) {
			this.interval = e.target.value;
		},
		durationChange(e) {
			this.duration = e.target.value;
		}
	}
};
</script>

<style lang="scss">
.paddingWrap {
	width: 690rpx;
	padding: 0 30rpx;
	.swiper {
		width: 100%;
		height: 300rpx;
		swiper-item, view {
			width: 100%;
			height: 100%;
			display: flex;
			align-items: center;
			justify-content: center;
		}
	}
	.listCell {
		width: 100%;
		height: auto;
		padding: 30rpx 0;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
}
</style>
