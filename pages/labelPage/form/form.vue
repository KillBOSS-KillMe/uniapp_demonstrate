<template>
    <view>
        <view>
            <form @submit="formSubmit" @reset="formReset">
                <view class="paddingWrap">
                    <view class="title">switch</view>
                    <view>
                        <switch name="switch" />
                    </view>
                </view>
                <view class="paddingWrap">
                    <view class="title">radio</view>
                    <radio-group name="radio">
                        <label>
                            <radio value="radio1" /><text>选项一</text>
                        </label>
                        <label>
                            <radio value="radio2" /><text>选项二</text>
                        </label>
                    </radio-group>
                </view>
                <view class="paddingWrap">
                    <view class="title">checkbox</view>
                    <checkbox-group name="checkbox">
                        <label>
                            <checkbox value="checkbox1" /><text>选项一</text>
                        </label>
                        <label>
                            <checkbox value="checkbox2" /><text>选项二</text>
                        </label>
                    </checkbox-group>
                </view>
                <view class="paddingWrap">
                    <view class="title">slider</view>
                    <slider value="50" name="slider" show-value></slider>
                </view>
                <view class="paddingWrap">
                    <view class="title">input</view>
                    <input class="uni-input" name="input" placeholder="这是一个输入框" />
                </view>
                <view class="uni-btn-v">
					<button form-type="submit" type="primary">Submit</button>
                    <button type="default" form-type="reset">Reset</button>
                </view>
            </form>
        </view>
    </view>
</template>
<script>
    export default {
        data() {
            return {
            }
        },
        methods: {
            formSubmit: function(e) {
                console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
                var formdata = e.detail.value
                uni.showModal({
                    content: '表单数据内容：' + JSON.stringify(formdata),
                    showCancel: false
                });
            },
            formReset: function(e) {
                console.log('清空数据')
            }
        }
    }
</script>

<style lang="scss">
.paddingWrap {
	width: 690rpx;
	padding: 0 30rpx;
	}
	.title {
		margin: 30rpx 0;
		font-size: $titleSize_1;
		color: $mainFontColor;
		font-weight: $mainFontWeight;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}
	button {
		margin: 20rpx 0;
	}
	input {
		border: 1rpx solid $borderColor;
		padding: 10rpx;
	}
    .uni-form-item .title {
        padding: 20rpx 0;
    }
</style>