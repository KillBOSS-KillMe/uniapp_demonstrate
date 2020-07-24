<template>
    <view>
        <view class="page-body">
            <view class="btn-area">
                <navigator url="navigate/navigate?title=navigate" hover-class="navigator-hover">
                    <button type="default">跳转到新页面</button>
                </navigator>
                <navigator url="redirect/redirect?title=redirect" open-type="redirect" hover-class="other-navigator-hover">
                    <button type="default">在当前页打开</button>
                </navigator>
                <navigator url="/pages/tabBar/extUI/extUI" open-type="switchTab" hover-class="other-navigator-hover">
                    <button type="default">跳转tab页面</button>
                </navigator>
            </view>
        </view>
    </view>
</template>

<script>
	export default {
	    onLoad: function (option) { //option为object类型，会序列化上个页面传递的参数
	        console.log(option.id); //打印出上个页面传递的参数。
	        console.log(option.name); //打印出上个页面传递的参数。
	    }
	}
</script>

<style lang="scss">

</style>
