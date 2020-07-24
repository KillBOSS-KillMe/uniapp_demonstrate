<template>
    <view class="tabBar">
        <view class="headerLogo"><image src="/static/images/extuiIndex.png"></image></view>
		<view class="doc">
			<text>以下将演示uni-app接口能力，详细文档见：</text>
			<u-link :href="'https://ext.dcloud.net.cn/'" :text="'https://ext.dcloud.net.cn/'" :inWhiteList="true"></u-link>
		</view>
		<view class="labelTypeList" v-for="(item, index) in list" :key="item.id">
			<view class="typeItem" @click="triggerCollapse(index)">
				<text>{{ item.name }}</text>
				<icon class="iconfont iconxiangyou"></icon>
			</view>
		</view>
    </view>
</template>
<script>
	import Extui from './extui-model.js';
	const extui = new Extui();
    import uLink from '@/components/u-link/u-link.vue'
    export default {
        components: {
            uLink
        },
        data() {return {
                // list: list,
                navigateFlag: false,
				list: [{
							name: "Badge 数字角标",
							url: "badge"
						},
						{
							name: "Calendar 日历",
							url: "calendar"
						},
						{
							name: "Card 卡片",
							url: "card"
						},
						{
							name: "Collapse 折叠面板",
							url: "collapse"
						},
						{
							name: "Combox 组合框",
							url: "combox"
						},
						{
							name: "Countdown 倒计时",
							url: "countdown"
						},
						{
							name: "Drawer 抽屉",
							url: "drawer"
						},
						{
							name: "Fab 悬浮按钮",
							url: "fab"
						},
						{
							name: "Fav 收藏按钮",
							url: "fav"
						},
						{
							name: "GoodsNav 商品导航",
							url: "goods-nav"
						},
						{
							name: "Grid 宫格",
							url: "grid"
						},
						{
							name: "Icons 图标",
							url: "icons"
						},
						{
							name: "IndexedList 索引列表",
							url: "indexed-list"
						},
						{
							name: "Link 超链接",
							url: "link"
						},
						{
							name: "List 列表",
							url: "list"
						},
						{
							name: "LoadMore 加载更多",
							url: "load-more"
						},
						{
							name: "NavBar 自定义导航栏",
							url: "nav-bar"
						},
						// #ifndef QUICKAPP-WEBVIEW
						{
							name: "NoticeBar 通告栏",
							url: "notice-bar"
						},
						// #endif
						{
							name: "NumberBox 数字输入框",
							url: "number-box"
						},
						{
							name: "Pagination 分页器",
							url: "pagination"
						},
						// #ifndef QUICKAPP-WEBVIEW-HUAWEI
						{
							name: "PopUp 弹出层",
							url: "popup"
						},
						// #endif
						{
							name: "Rate 评分",
							url: "rate"
						},
						{
							name: "SearchBar 搜索栏",
							url: "search-bar"
						},
						{
							name: "SegmentedControl 分段器",
							url: "segmented-control"
						},
						{
							name: "Steps 步骤条",
							url: "steps"
						},
						{
							name: "SwipeAction 滑动操作",
							url: "swipe-action"
						},
						{
							name: "SwiperDot 轮播图指示点",
							url: "swiper-dot"
						},
						{
							name: "Tag 标签",
							url: "tag"
						},
						{
							name: "Transition 过渡动画",
							url: "transition"
						},
					]
				
            };
        },
        onShareAppMessage() {
			Extui.onShareAppMessage()
        },
        onLoad() {
        },
        onReady() {
        },
        onShow() {
        },
        onHide() {
        },
        methods: {
            triggerCollapse(index) {
                index.navigate_to(this.list[index].url);
            }
        }
    };
</script>

<style>
</style>
