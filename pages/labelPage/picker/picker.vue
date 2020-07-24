<template>
	<view class="paddingWrap">
		<view class="title">地区选择器</view>
		<view class="title">
			<view class="uni-list-cell-left">当前选择</view>
			<picker @change="bindPickerChange" :value="index" :range="array">
				<view class="uni-input">{{ array[index] }}</view>
			</picker>
		</view>

		<view class="title">时间选择器</view>
		<view class="title">
			<view class="uni-list-cell-left">当前选择</view>
			<picker mode="time" :value="time" start="09:01" end="21:01" @change="bindTimeChange">
				<view class="uni-input">{{ time }}</view>
			</picker>
		</view>

		<view class="title">日期选择器</view>
		<view class="title">
			<view class="uni-list-cell-left">当前选择</view>
			<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
				<view class="uni-input">{{ date }}</view>
			</picker>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		const currentDate = this.getDate({
			format: true
		});
		return {
			title: 'picker',
			array: ['中国', '美国', '巴西', '日本'],
			index: 0,
			date: currentDate,
			time: '12:01'
		};
	},
	computed: {
		startDate() {
			return this.getDate('start');
		},
		endDate() {
			return this.getDate('end');
		}
	},
	methods: {
		bindPickerChange: function(e) {
			console.log('picker发送选择改变，携带值为', e.target.value);
			this.index = e.target.value;
		},
		bindDateChange: function(e) {
			this.date = e.target.value;
		},
		bindTimeChange: function(e) {
			this.time = e.target.value;
		},
		getDate(type) {
			const date = new Date();
			let year = date.getFullYear();
			let month = date.getMonth() + 1;
			let day = date.getDate();

			if (type === 'start') {
				year = year - 60;
			} else if (type === 'end') {
				year = year + 2;
			}
			month = month > 9 ? month : '0' + month;
			day = day > 9 ? day : '0' + day;
			return `${year}-${month}-${day}`;
		}
	}
};
</script>

<style lang="scss">
	.paddingWrap{
		width:690rpx;
		padding:30rpx;
		.title {
			margin: 30rpx 0;
			font-size: $titleSize_1;
			color: $mainFontColor;
			font-weight: $mainFontWeight;
			display: flex;
			align-items: center;
			justify-content: flex-start;
			picker {
				margin-left: 30rpx;
				box-shadow: #f1fefb 1rpx 1rpx 10rpx 5rpx;
			}
		}
	}
</style>
