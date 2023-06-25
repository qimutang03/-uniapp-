<template>
	<!-- 轮播图 -->
	<view class="home">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" :circular="true">
			<swiper-item class="swiper-item" v-for="item in swipers" :key="item.id">
				<image :src="item.img"></image>
			</swiper-item>
			<!-- <swiper-item class="swiper-item">
				<image class="swiper-item">2</image>
			</swiper-item> -->
		</swiper>
		<!-- 导航区域 -->
		<view class="nav">
			<!-- <view class="nav_item" v-for="(item, index) in navs" :key="index">
				<view class="tubiao-icons">{{item.icon}}</view>
				<text>{{item.title}}</text>
			</view> -->
			<view class="nav_item" @click="navItemClick()">
				<view class="tubiao-icons"><uni-icons type="center" size="30"></uni-icons></uni-icons></view>
				<text>超市</text>
			</view>
			<view class="nav_item" @click="myItemClick()">
				<view><uni-icons type="contact" size="30"></uni-icons></view>
				<text>我们</text>
			</view>
			<view class="nav_item" @click="imgItemClick()">
				<view><uni-icons type="image" size="30"></uni-icons></view>
				<text>图片</text>
			</view>
			<view class="nav_item" @click="vidItemClick()">
				<view><uni-icons type="videocam" size="30"></uni-icons></view>
				<text>视频</text>
			</view>
		</view>
		<!-- 推荐商品 -->
		<view class="hot_goods">
			<view class="tit">推荐商品</view>
			<goods-list :goods="goods"></goods-list>
		</view>
	</view>
</template>

<script>
	import goodsList from '../../components/goods-list/goods-list.vue'
	export default {
		data() {
			return {
				swipers: [],
				goods: [],
				navs: [
					{icon: 'center',
					title:'超市',
					path: 'pages/goods/goods',
					},
					{icon: 'contact',
					title:'我们',
					path: 'pages/contact/contact',
					},
					{icon: 'image',
					title:'图片',
					path: 'pages/pics/pics',
					},
					{icon: 'tubiao-icons',
					title:'视频',
					path: 'pages/videos/videos',
					}
				]
			}
		},
		onLoad() {
			this.getSwipers()
			this.getHotgoods()
		},
		components:{"goods-list":goodsList},
		methods: {
			// getSwipers() {
			// 	console.log('获取数据')
			// 	uni.request({
			// 		url:"http://localhost:8082/api/getlunbo",
			// 		success: (res) => {
			// 			console.log(res)
			// 			if(res.data.status != 0) {
			// 				return uni.showToast({
			// 					title:'获取数据失败'
			// 				})
			// 			}
			// 			this.swipers = res.data.message
			// 		}
			// 	})
			// }
			// 获取轮播图数据
			async getSwipers() {
				const res =  await this.$myRuquest({
					url:'/api/getlunbo'
				})
				this.swipers = res.data.message
				console.log(this.swipers)
			},
			// 获取热门商品列表数据
			async getHotgoods(){
				const res = await this.$myRuquest({
					url:'/api/getgoods?pageindex=1'
				})
				this.goods = res.data.message
				console.log(res)
			},
			// 点击跳转页面
			navItemClick() {
				uni.navigateTo({
					url:'../goods/goods',
				})
			},
			myItemClick() {
				uni.navigateTo({
					url:'../contact/contact',
				})
			},
			imgItemClick() {
				uni.navigateTo({
					url:'../pics/pics',
				})
			},
			vidItemClick() {
				uni.navigateTo({
					url:'../videos/videos',
				})
			}
		}
	}
</script>

<style lang="scss">
	.home{
		swiper{
			height: 380rpx;
			width: 750rpx;
			image{
				width: 100%;
				height: 100%;
				margin: auto;
				display: block;
			}
		}
		.nav{
			display: flex;
			.nav_item{
				width: 25%;
				text-align: center;
				view{
					width: 80rpx;
					height: 80rpx;
					background: #B50E03;
					border-radius: 60rpx;
					margin: 10rpx auto;
					
				}
				text{
					font-size: 30rpx;
				}
			}
		}
		.hot_goods{
			background: #eee;
			overflow: hidden;
		}
		.tit{
			height: 50px;
			line-height: 50px;
			color: $shop-color;
			text-align: center;
			letter-spacing: 20px;
			background: #fff;
			margin: 10rpx 0;
		}
		
	}
</style>
