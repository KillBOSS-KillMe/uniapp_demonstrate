<template>
    <view class="tabBar">
        <view class="headerLogo"><image src="/static/images/apiIndex.png"></image></view>
		<view class="doc">
			<text>以下将演示uni-app接口能力，详细文档见：</text>
			<u-link :href="'https://uniapp.dcloud.io/api/'" :text="'https://uniapp.dcloud.io/api/'" :inWhiteList="true"></u-link>
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
	import Api from './api-model.js';
	const api = new Api();
    import uLink from '@/components/u-link/u-link.vue'
    export default {
        components: {
            uLink
        },
        data() {
            // 暂时这么写，后面看怎么优化。
            let mediaPages = [{
                    name: '图片',
                    url: 'image'
                },
				{
				    name: '音频',
				    url: 'inner-audio'
				},
                // #ifdef APP-PLUS || MP-WEIXIN || MP-BAIDU || MP-QQ
                {
                    name: '录音',
                    url: 'voice'
                },
                {
                    name: '背景音频',
                    url: 'background-audio'
                },
                // #endif
                // #ifndef MP-ALIPAY
                {
                    name: '视频',
                    url: 'video'
                },
                // #endif
                // #ifndef H5
                {
                    name: '文件',
                    url: 'file'
                },
                // #endif
                // #ifndef H5 || MP-ALIPAY
                {
                    name: '保存媒体到本地',
                    url: 'save-media'
                }
                // #endif
            ];

            const list = [{
                    id: 'page',
                    name: '界面',
                    open: false,
                    pages: [{
                            name: '设置导航条',
                            url: 'set-navigation-bar-title'
                        },
                        //#ifdef APP-PLUS
                        {
                            name: '原生子窗体',
                            url: 'subnvue'
                        },
                        //#endif
                        {
                            name: '页面跳转',
                            url: 'navigator'
                        },
                        //#ifndef MP-TOUTIAO
                        {
                            name: '设置TabBar',
                            url: 'set-tabbar'
                        },
                        //#endif
                        {
                            name: '下拉刷新',
                            url: 'pull-down-refresh'
                        },
                        {
                            name: '创建动画',
                            url: 'animation'
                        },
						// #ifndef QUICKAPP-WEBVIEW-UNION
                        {
                            name: '创建绘画',
                            url: 'canvas'
                        },
						// #endif
                        {
                            name: '节点信息',
                            url: 'get-node-info'
                        },
                        {
                            name: '节点布局交互状态',
                            url: 'intersection-observer'
                        },
                        {
                            name: '显示操作菜单',
                            url: 'action-sheet'
                        },
                        {
                            name: '显示模态弹窗',
                            url: 'modal'
                        },
                        {
                            name: '显示加载提示框',
                            url: 'show-loading'
                        },
                        {
                            name: '显示消息提示框',
                            url: 'toast'
                        }
                    ]
                },
                {
                    id: 'device',
                    name: '设备',
                    open: false,
                    pages: [{
                            name: '获取手机网络状态',
                            url: 'get-network-type'
                        },
                        {
                            name: '获取手机系统信息',
                            url: 'get-system-info'
                        },
                        {
                            name: '打电话',
                            url: 'make-phone-call'
                        },
                        //#ifndef H5
                        {
                            name: '震动',
                            url: 'vibrate'
                        },
                        {
                            name: '添加手机联系人',
                            url: 'add-phone-contact'
                        },
                        {
                            name: '扫码',
                            url: 'scan-code'
                        },
                        {
                            name: '剪贴板',
                            url: 'clipboard'
                        },
                        //#endif
                        // #ifndef H5 || MP-ALIPAY
                        {
                            name: '屏幕亮度',
                            url: 'brightness'
                        },
                        // #endif
                        // #ifdef APP-PLUS || MP-WEIXIN || MP-QQ
                        {
                            name: '蓝牙',
                            url: 'bluetooth'
                        },
                        {
                            name: '生物认证',
                            url: 'soter'
                        },
                        // #endif
                        // #ifdef APP-PLUS || MP-WEIXIN
                        {
                            name: 'iBeacon',
                            url: 'ibeacon'
                        },
                        // #endif
                        {
                            name: '监听加速度传感器',
                            url: 'on-accelerometer-change'
                        },
                        {
                            name: '监听罗盘数据',
                            url: 'on-compass-change'
                        },
                        //#ifdef APP-PLUS
                        {
                            name: '监听距离传感器',
                            url: '/platforms/app-plus/proximity/proximity'
                        },
                        {
                            name: '监听方向传感器',
                            url: '/platforms/app-plus/orientation/orientation'
                        }
                        //#endif
                    ]
                },
                {
                    id: 'network',
                    name: '网络',
                    open: false,
                    pages: [{
                            name: '发起一个请求',
                            url: 'request'
                        },
                        {
                            name: '上传文件',
                            url: 'upload-file'
                        },
                        {
                            name: '下载文件',
                            url: 'download-file'
                        }
                    ]
                },
                {
                    id: 'websocket',
                    name: 'websocket',
                    open: false,
                    pages: [
                        // #ifndef MP-ALIPAY
                        {
                            name: 'socketTask',
                            url: 'websocket-socketTask'
                        },
                        // #endif
                        {
                            name: '全局websocket',
                            url: 'websocket-global'
                        }
                    ]
                },
                {
                    id: 'media',
                    name: '媒体',
                    open: false,
                    pages: mediaPages
                },
                {
                    id: 'location',
                    name: '位置',
                    open: false,
                    pages: [{
                            name: '获取当前位置',
                            url: 'get-location'
                        },
                        {
                            name: '使用地图查看位置',
                            url: 'open-location'
                        },
                        // #ifndef MP-TOUTIAO
                        {
                            name: '使用地图选择位置',
                            url: 'choose-location'
                        }
                        // #endif
                        // #ifndef MP-QQ || MP-TOUTIAO
                        ,
                        {
                            name: '地图控制',
                            url: 'map'
                        }
                        // #endif
                        // #ifdef APP-PLUS
                        ,
                        {
                            name: '地图搜索',
                            url: 'map-search'
                        }
                        // #endif
                    ]
                },
                {
                    id: 'storage',
                    name: '数据',
                    open: false,
                    pages: [{
                            name: '数据存储（key-value）',
                            url: 'storage'
                        },
                        // #ifdef APP-PLUS
                        {
                            name: 'SQLite',
                            url: 'sqlite'
                        }
                        // #endif
                    ]
                },
                // #ifdef APP-PLUS || MP-WEIXIN
                {
                    url: 'rewarded-video-ad',
                    name: '激励视频广告',
                    open: false
                },
                // #endif
                // #ifndef H5 || QUICKAPP-WEBVIEW
                {
                    id: 'login',
                    name: '登录',
                    open: false,
                    pages: [{
                            name: '登录',
                            url: 'login'
                        },
                        {
                            name: '获取用户信息',
                            url: 'get-user-info'
                        }
                    ]
                },
				// #endif
				// #ifndef H5 || QUICKAPP-WEBVIEW-UNION
                {
                    id: 'share',
                    name: '分享',
                    open: false,
                    pages: [{
                        name: '分享',
                        url: 'share'
                    }]
                },
                // #endif
                // #ifdef APP-PLUS || MP-WEIXIN
                {
                    id: 'payment',
                    name: '支付',
                    open: false,
                    pages: [{
                        name: '发起支付',
                        url: 'request-payment'
                    }]
                },
                // #endif
                // #ifdef APP-PLUS
                {
                    id: 'speech',
                    name: '语音',
                    open: false,
                    pages: [{
                        name: '语音识别',
                        url: '/platforms/app-plus/speech/speech'
                    }]
                },
                {
                    id: 'push',
                    name: '推送',
                    open: false,
                    pages: [{
                        name: '推送',
                        url: '/platforms/app-plus/push/push'
                    }]
                }
                //#endif
            ];
            return {
                list: list,
                navigateFlag: false
            };
        },
        onShareAppMessage() {
			api.onShareAppMessage()
        },
        onLoad() {
        },
        onReady() {
        },
        onShow() {
            this.navigateFlag = false;
        },
        onHide() {
        },
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

<style>
</style>
