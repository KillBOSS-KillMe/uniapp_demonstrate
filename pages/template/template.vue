<template>
	<view class="tabBar">
		<view class="headerLogo"><image src="/static/images/templateIndex.png"></image></view>
		<view class="doc">
			<text>以下将演示uni-app接口能力，详细文档见：</text>
			<u-link :href="'https://ext.dcloud.net.cn'" :text="'https://ext.dcloud.net.cn'" :inWhiteList="true"></u-link>
		</view>
		<view class="labelTypeList" v-for="(item, index) in list" :key="item.id">
			<view class="typeItem" :class="item.open ? 'active' : ''" @click="triggerCollapse(index)">
				<text>{{ item.name }}</text>
				<icon class="iconfont iconarrow_down" :class="item.open ? 'panelIconOn' : ''"></icon>
			</view>
			<view class="typeList" v-if="item.open">
				<view class="typeCon" v-for="(item2, key) in item.pages" :key="key" @click="goDetailPage(item2)">
					<text class="uni-navigate-text">{{ item2.name ? item2.name : item2 }}</text>
					<icon class="iconfont iconxiangyou"></icon>
				</view>
			</view>
		</view>
	</view>
</template>
<script>
import Template from './template-model.js';
const template = new Template();
import uLink from '@/components/uLink.vue';
export default {
	components: {
		uLink
	},
	data() {
		return {
			list: [
				// #ifdef APP-PLUS || H5 || MP-ALIPAY
				{
					id: 'navbar',
					name: '顶部原生导航标题栏',
					open: false,
					pages: [
						// #ifdef APP-PLUS || H5
						{
							name: '导航栏带自定义按钮',
							url: 'nav-button'
						},
						{
							name: '导航栏带红点和角标',
							url: 'nav-dot'
						},
						{
							name: '导航栏带城市选择',
							url: 'nav-city-dropdown'
						},
						{
							name: '导航栏带搜索框',
							url: 'nav-search-input'
						},
						// #endif
						// #ifdef APP-PLUS || H5 || MP-ALIPAY
						{
							name: '透明渐变样式',
							url: 'nav-transparent'
						},
						{
							name: '导航栏带图片',
							url: 'nav-image'
						}
						// #endif
					]
				},
				// #endif
				// #ifndef QUICKAPP-WEBVIEW
				{
					name: '顶部选项卡',
					url: 'tabbar'
				},
				// #endif
				{
					name: '组件通讯',
					url: 'component-communication'
				},
				// #ifndef MP-QQ || QUICKAPP-WEBVIEW
				{
					name: 'uCharts 图表',
					url: 'ucharts'
				},
				// #endif
				// #ifndef QUICKAPP-WEBVIEW
				{
					name: '列表到详情示例',
					url: 'list2detail-list'
				},
				// #endif
				// #ifdef APP-PLUS || H5 || MP-WEIXIN  || MP-QQ
				{
					name: '上下滑动切换视频',
					url: 'swiper-vertical'
				},
				// #endif
				// #ifdef APP-NVUE
				{
					name: 'swiper-list',
					url: 'swiper-list-nvue'
				},
				// #endif
				{
					name: 'GlobalData和vuex',
					url: 'global'
				},
				// #ifdef APP-PLUS
				{
					name: '问题反馈',
					url: '/platforms/app-plus/feedback/feedback'
				},
				{
					name: '打开外部应用',
					url: 'scheme'
				},
				// #endif
				// #ifdef APP-PLUS || MP-WEIXIN || MP-QQ || H5
				{
					name: '微信自定义组件示例（vant ui）',
					url: 'vant-button'
				}
				// #endif
			],
			navigateFlag: false
		};
	},
	onShareAppMessage() {
		template.onShareAppMessage();
	},
	onLoad() {},
	onReady() {},
	onShow() {
		this.navigateFlag = false;
	},
	onHide() {},
	methods: {
		triggerCollapse(e) {
			if (!this.list[e].pages) {
				this.goDetailPage(this.list[e].url);
				return;
			}
			for (var i = 0; i < this.list.length; ++i) {
				if (e === i) {
					this.list[i].open = !this.list[e].open;
				} else {
					this.list[i].open = false;
				}
			}
		},
		goDetailPage(e) {
			if (this.navigateFlag) {
				return;
			}
			this.navigateFlag = true;
			if (e === 'set-tabbar') {
				return;
			}
			let url = ~e.indexOf('platform') ? e : '/pages/API/' + e + '/' + e;
			index.navigate_to(url);
		}
	}
};
</script>

<style></style>
