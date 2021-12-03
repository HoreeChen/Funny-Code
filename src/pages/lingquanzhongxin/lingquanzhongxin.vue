<template>
	<view>
		<view class="top">领券中心</view>
	</view>
</template>

<script>
	import { couponList, couponReceive } from '@/api/userInfo';
	export default {
		data() {
			return {
				couponList: [],
				type: null,
				loadingType: 'more',
				page: 1,
				loading: true,
				moneySymbol: this.moneySymbol,
				errorInfo: '',
			}
		},
		onLoad() {
			// this.type = options.type;
			this.initData();
			console.log(this.couponList)
		},
		methods: {
			initData() {
				this.getCouponH();
			},
			getCouponH(){
				uni.request({
				    url: 'http://demo.rageframe.com/api/tiny-shop/v1/marketing/coupon-type/index',
				    data: {
				        page: 3
				    },
				    header: {
				        'custom-header': 'hello' 
				    },
				    success: (res) => {
				        console.log(res.data);
				        this.text = 'request success';
				    }
				});
			},

			// 获取优惠券列表
			// async getCouponList(type) {
			// 	console.log(this.page)
			// 	await this.$http
			// 		.get(`${couponList}`, {
			// 			page: this.page
			// 		})
			// 		.then(r => {
			// 			this.loading = false;
			// 			if (type === 'refresh') {
			// 				uni.stopPullDownRefresh();
			// 			}
			// 			this.loadingType = r.data.length === 10 ? 'more' : 'nomore';
			// 			this.couponList = [...this.couponList, ...r.data];
			// 			console.log(this.couponList)
			// 		})
			// 		.catch(err => {
			// 			this.couponList.length = 0;
			// 			this.errorInfo = err;
			// 			this.loading = false;
			// 			if (type === 'refresh') {
			// 				uni.stopPullDownRefresh();
			// 			}
			// 		});
			// },
		},

	}
</script>

<style lang="scss">
	.top{
		height: 50rpx;
		width:750rpx;
		background-color: #FFFFFF;
		align-content: center;
	}

</style>
