<template>
	<view class="home">
		<swiper indicator-dots circular>
			<swiper-item v-for="item in swipers" :key="item.id">
				<image :src="item.image_src"></image>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swipers: []
			}
		},
		onLoad() {
			this.getSwipers()
		},
		methods: {
			//轮播图
			async getSwipers() {
				console.log('获取轮播图数据')
				const res = await this.$myRuquest({
					url: '/api/public/v1/home/swiperdata'
				})
				console.log(res.data.message)
				this.swipers = res.data.message
				console.log(this.swipers[0].image_src)
			}
		}
	}
</script>

<style lang="less">
.home{
	swiper{
		width: 750rpx;
		height: 380rpx;
		image{
			height: 100%;
			width: 100%;
		}
	}
}
</style>
