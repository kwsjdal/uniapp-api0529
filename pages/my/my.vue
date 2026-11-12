<template>
	<view class="my-container">
		<view class="header">
			<view class="back-btn" @click="goBack">
				<text class="back-icon">←</text>
			</view>
			<text class="title">我的</text>
		</view>
		<view class="button-list">
			<view class="button-item" @click="changeTabBarItem">
				<text class="button-text">更改tabBar</text>
			</view>
			<view class="button-item" @click="changeTabBarStyle">
				<text class="button-text">更改tabBar整体样式</text>
			</view>
			<view class="button-item" @click="hideTabBar">
				<text class="button-text">隐藏tabBar</text>
			</view>
			<view class="button-item" @click="showTabBar">
				<text class="button-text">显示tabBar</text>
			</view>
			<view class="button-item" @click="addBadge">
				<text class="button-text">右上角添加文本</text>
			</view>
			<view class="button-item" @click="removeBadge">
				<text class="button-text">删除右上角文本</text>
			</view>
			<view class="button-item" @click="showRedDot">
				<text class="button-text">显示右上角的红点</text>
			</view>
			<view class="button-item" @click="hideRedDot">
				<text class="button-text">隐藏右上角的红点</text>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			originalColor: '#7A7E83',
			originalBgColor: '#ffffff',
			currentColor: '#7A7E83',
			currentBgColor: '#ffffff'
		}
	},
	onLoad() {
		
	},
	methods: {
		goBack() {
			uni.reLaunch({
				url: '/pages/index/index'
			})
		},
		changeTabBarItem() {
			uni.setTabBarItem({
				index: 0,
				text: 'HOME',
				iconPath: 'static/tab_icons/咨询.png',
				selectedIconPath: 'static/tab_icons/咨询（1）.png'
			})
		},
		changeTabBarStyle() {
			let temp = this.currentColor
			this.currentColor = this.currentBgColor
			this.currentBgColor = temp
			
			uni.setTabBarStyle({
				color: this.currentColor,
				backgroundColor: this.currentBgColor,
				selectedColor: '#007AFF',
				borderStyle: 'black'
			})
		},
		hideTabBar() {
			uni.hideTabBar()
		},
		showTabBar() {
			uni.showTabBar()
		},
		addBadge() {
			uni.setTabBarBadge({
				index: 1,
				text: '9'
			})
		},
		removeBadge() {
			uni.removeTabBarBadge({
				index: 1
			})
		},
		showRedDot() {
			uni.showTabBarRedDot({
				index: 2
			})
		},
		hideRedDot() {
			uni.hideTabBarRedDot({
				index: 2
			})
		}
	}
}
</script>

<style>
.my-container {
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