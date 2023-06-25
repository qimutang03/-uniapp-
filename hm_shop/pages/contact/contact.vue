<template>
	<view class="contact">
		<img class="imgs" src="https://bpic.588ku.com/back_origin_min_pic/19/10/22/7d5760a4e3926576c237d950d5964db1.jpg" alt="">
		<view class="info">
			<view>联系电话：13114747116</view>
			<view>地址：中国广东省深圳市福田区中康路128号卓越城一期2号楼</view>
		</view>
		<map style="width: 100%; height: 300px;" :latitude="latitude" :longitude="longitude" :markers="covers"></map>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
.contact{
	.imgs{
		width: 750rpx;
		height: 320rpx;
	}
	.info{
		padding: 10rpx 20rpx;
		font-size: 30rpx;
		view{
			line-height: 70rpx;
			border-bottom: 2rpx solid #eee;
			
		}
	}
}
</style>
