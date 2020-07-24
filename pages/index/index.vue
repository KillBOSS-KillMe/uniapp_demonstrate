<template>
	<view class="tabBar">
		<view class="headerLogo"><image src="/static/images/componentIndex.png"></image></view>
		<view class="doc">
			<text>uni-app内置组件，展示样式仅供参考，文档详见：</text>
			<u-link :href="'https://uniapp.dcloud.io/component/'" :text="'https://uniapp.dcloud.io/component/'" :inWhiteList="true"></u-link>
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
import Index from './index-model.js';
const index = new Index();
import uLink from '@/components/uLink.vue';
export default {
	components: {
		uLink
	},
	data() {
		return {
			list: [
				{
					id: 'view',
					name: '视图容器',
					open: false,
					pages: [
						'view',
						'scroll-view',
						'swiper',
						// #ifndef MP-TOUTIAO
						'movable-view',
						'cover-view'
						// #endif
					]
				},
				{
					id: 'content',
					name: '基础内容',
					open: false,
					pages: ['text', 'rich-text', 'progress']
				},
				{
					id: 'form',
					name: '表单组件',
					open: false,
					pages: [
						'button',
						'checkbox',
						'form',
						'input',
						'label',
						'picker',
						'picker-view',
						'radio',
						'slider',
						'switch',
						'textarea',
						// #ifdef APP-PLUS || MP-WEIXIN || H5
						'editor'
						// #endif
					]
				},
				{
					id: 'nav',
					name: '导航',
					open: false,
					pages: ['navigator']
				},
				{
					id: 'media',
					name: '媒体组件',
					open: false,
					pages: [
						'image',
						'video',
						// #ifndef MP-ALIPAY || MP-TOUTIAO
						'audio'
						// #endif
					]
				},
				// #ifndef MP-TOUTIAO
				{
					id: 'map',
					name: '地图',
					open: false,
					pages: ['map']
				},
				// #endif
				// #ifndef QUICKAPP-WEBVIEW-UNION
				{
					id: 'canvas',
					name: '画布',
					open: false,
					pages: ['canvas']
				},
				// #endif
				// #ifdef APP-PLUS || H5
				{
					id: 'web-view',
					name: '网页',
					open: false,
					pages: [
						{
							name: '网络网页',
							url: '/pages/component/web-view/web-view'
						},
						{
							name: '本地网页',
							url: '/pages/component/web-view-local/web-view-local'
						}
					]
				},
				// #endif
				// #ifndef APP-PLUS || H5
				{
					id: 'web-view',
					name: '网页',
					open: false,
					pages: ['web-view']
				},
				// #endif
				// #ifndef H5 || MP-BAIDU || QUICKAPP-WEBVIEW
				{
					url: 'ad',
					name: 'AD组件',
					open: false
				}
				// #endif
			],
			navigateFlag: false
		};
	},
	onShareAppMessage() {
		return {
			title: '欢迎体验uni-app',
			path: '/pages/component/component'
		};
	},
	methods: {
		triggerCollapse(index) {
			if (!this.list[index].pages) {
				this.goDetailPage(this.list[index].url);
				return;
			}
			for (var i = 0; i < this.list.length; ++i) {
				if (index === i) {
					this.list[i].open = !this.list[index].open;
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
			if (typeof e === 'string') {
				index.navigate_to('/pages/labelPage/' + e + '/' + e);
			} else {
				index.navigate_to(e.url);
			}
			setTimeout(() => {
				this.navigateFlag = false;
			}, 200);
		}
	}
};
</script>

<style lang="scss">

</style>
