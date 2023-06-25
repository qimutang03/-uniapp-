<template>
	<!-- <view> -->
		<view class="goods_list">
			<view class="goods_item" v-for="item in goods" :key="item.id">
				<image :src="item.img_url"></image>
				<view class="price">
					<text>￥{{item.sell_price}}</text>
					<text class="price_two">￥{{item.market_price}}</text>
				</view>
				<view class="name">
					{{item.title}}
				</view>
			</view>
			
		</view>
	<!-- </view> -->
</template>

<script>
	export default {
		data() {
			return {
				props: ['goods']
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.goods_list{
			padding: 0 15rpx;
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			.goods_item{
				background: #fff;
				width: 355rpx;
				margin: 10rpx 0;
				padding: 15rpx;
				box-sizing: border-box;
				image{
					width: 80%;
					height: 150rpx;
				}
				.price{
					color: $shop-color;
					font-size: 36rpx;
					text:nth-child(2){
						color: #ccc;
						font-size: 30rpx;
						margin-left: 10rpx;
						text-decoration: line-through;
					}
				}
				.name{
					font-size: 30rpx;
					height: 50rpx;
					padding-top: 10rpx;
					padding-bottom: 15rpx;
				}
			}
			
		}
</style>
