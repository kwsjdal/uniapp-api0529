<template>
	<view class="cart-container">
		<view class="header">
			<view class="back-btn" @click="goBack">
				<text class="back-icon">←</text>
			</view>
			<text class="title">购物车</text>
		</view>
		<scroll-view 
			class="goods-scroll" 
			scroll-y 
			refresher-enabled 
			:refresher-triggered="refresherTriggered"
			@refresherrefresh="onPullDownRefresh"
		>
			<view class="goods-list">
				<view class="goods-item" v-for="(item, index) in goodsList" :key="index">
					<image class="goods-image" :src="item.image" mode="aspectFill"></image>
					<view class="goods-info">
						<text class="goods-name">{{ item.name }}</text>
						<text class="goods-price">¥{{ item.price }}</text>
						<text class="goods-count">数量: {{ item.count }}</text>
					</view>
				</view>
				<view v-if="goodsList.length === 0" class="empty-text">购物车为空</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			refresherTriggered: false,
			goodsList: [
				{
					name: '商品1 - 智能手机',
					price: 2999,
					count: 1,
					image: '/static/logo.png'
				},
				{
					name: '商品2 - 蓝牙耳机',
					price: 299,
					count: 2,
					image: '/static/logo.png'
				},
				{
					name: '商品3 - 智能手表',
					price: 1299,
					count: 1,
					image: '/static/logo.png'
				},
				{
					name: '商品4 - 平板电脑',
					price: 3999,
					count: 1,
					image: '/static/logo.png'
				},
				{
					name: '商品5 - 无线鼠标',
					price: 99,
					count: 3,
					image: '/static/logo.png'
				},
				{
					name: '商品6 - 机械键盘',
					price: 599,
					count: 1,
					image: '/static/logo.png'
				},
				{
					name: '商品7 - 游戏手柄',
					price: 299,
					count: 2,
					image: '/static/logo.png'
				},
				{
					name: '商品8 - 显示器',
					price: 1999,
					count: 1,
					image: '/static/logo.png'
				}
			]
		}
	},
	onLoad() {
		console.log('Cart page loaded')
	},
	onPullDownRefresh() {
		console.log('页面级下拉刷新触发')
	},
	methods: {
		goBack() {
			uni.reLaunch({
				url: '/pages/index/index'
			})
		},
		onPullDownRefresh() {
			console.log('scroll-view下拉刷新触发')
			this.refresherTriggered = true
			
			setTimeout(() => {
				const newGoods = [
					{
						name: '商品' + (this.goodsList.length + 1) + ' - 笔记本电脑',
						price: 5999,
						count: 1,
						image: '/static/logo.png'
					},
					{
						name: '商品' + (this.goodsList.length + 2) + ' - 无线耳机',
						price: 799,
						count: 1,
						image: '/static/logo.png'
					}
				]
				this.goodsList = [...this.goodsList, ...newGoods]
				this.refresherTriggered = false
				console.log('下拉刷新停止，商品数量:', this.goodsList.length)
			}, 1500)
		}
	}
}
</script>

<style>
.cart-container {
	display: flex;
	flex-direction: column;
	height: 100vh;
	background-color: #f5f5f5;
}

.header {
	width: 100%;
	padding: 20rpx;
	background-color: #007AFF;
	display: flex;
	align-items: center;
	position: fixed;
	top: 0;
	left: 0;
	z-index: 100;
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

.goods-scroll {
	flex: 1;
	padding-top: 100rpx;
}

.goods-list {
	padding: 20rpx;
}

.goods-item {
	display: flex;
	background-color: #ffffff;
	padding: 20rpx;
	margin-bottom: 10rpx;
	border-radius: 10rpx;
}

.goods-image {
	width: 150rpx;
	height: 150rpx;
	border-radius: 10rpx;
	background-color: #eeeeee;
}

.goods-info {
	flex: 1;
	display: flex;
	flex-direction: column;
	padding-left: 20rpx;
	justify-content: space-around;
}

.goods-name {
	font-size: 28rpx;
	color: #333333;
	font-weight: bold;
}

.goods-price {
	font-size: 26rpx;
	color: #FF5722;
}

.goods-count {
	font-size: 24rpx;
	color: #999999;
}

.empty-text {
	text-align: center;
	color: #999999;
	padding: 100rpx 0;
}
</style>