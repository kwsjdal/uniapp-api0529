<template>
	<view class="home-container">
		<view class="header">
			<view class="back-btn" v-if="showBackBtn" @click="goBack">
				<text class="back-icon">←</text>
			</view>
			<text class="title">首页</text>
		</view>
		<view class="button-list">
			<view class="button-item" @click="setNavigationBarTitle">
				<text class="button-text">设置页面标题</text>
			</view>
			<view class="button-item" @click="setNavigationBarColor">
				<text class="button-text">设置导航条颜色</text>
			</view>
			<view class="button-item" @click="showNavigationBarLoading">
				<text class="button-text">显示导航条加载动画</text>
			</view>
			<view class="button-item" @click="hideNavigationBarLoading">
				<text class="button-text">隐藏导航条加载动画</text>
			</view>
			<view class="button-item" @click="hideHomeButton">
				<text class="button-text">隐藏返回按钮</text>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			showBackBtn: true
		}
	},
	onLoad() {
		console.log('Home page loaded')
	},
	methods: {
		goBack() {
			console.log('goBack clicked')
			uni.reLaunch({
				url: '/pages/index/index'
			})
		},
		setNavigationBarTitle() {
			console.log('setNavigationBarTitle clicked')
			uni.setNavigationBarTitle({
				title: '新标题'
			})
		},
		setNavigationBarColor() {
			console.log('setNavigationBarColor clicked')
			uni.setNavigationBarColor({
				frontColor: '#ffffff',
				backgroundColor: '#FF5722'
			})
		},
		showNavigationBarLoading() {
			console.log('showNavigationBarLoading clicked')
			uni.showNavigationBarLoading()
		},
		hideNavigationBarLoading() {
			console.log('hideNavigationBarLoading clicked')
			uni.hideNavigationBarLoading()
		},
		hideHomeButton() {
			console.log('hideHomeButton clicked')
			this.showBackBtn = false
		}
	}
}
</script>

<style>
.home-container {
	display: flex;
	flex-direction: column;
	min-height: 100vh;
	background-color: #f5f5f5;
}

.header {
	width: 100%;
	padding: 20rpx;
	background-color: #007AFF;
	display: flex;
	align-items: center;
}

.back-btn {
	width: 60rpx;
	height: 60rpx;
	display: flex;
	align-items: center;
	justify-content: center;
}

.back-icon {
	font-size: 36rpx;
	color: #ffffff;
}

.title {
	flex: 1;
	font-size: 36rpx;
	color: #ffffff;
	font-weight: bold;
	text-align: center;
	margin-right: 60rpx;
}

.button-list {
	padding: 20rpx;
	flex: 1;
}

.button-item {
	background-color: #ffffff;
	padding: 30rpx;
	margin-bottom: 1rpx;
	text-align: center;
}

.button-text {
	font-size: 32rpx;
	color: #333333;
}
</style>