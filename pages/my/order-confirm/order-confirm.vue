<template>
	<view style="background: #F5F5F5;min-height: 100%;height: auto;">
		<!-- 地址选择 -->
		<view class="main-bg-color text-white d-flex a-center px-3" style="height: 250rpx;" hover-class="main-bg-hover-color"  @click="openPathList">
			<view>
				<template v-if="path">
					<view class="font-weight font-md d-flex a-center font-lg">
					    {{path.name}}{{path.phone}}
						<view class="border border-white rounded px-1 font ml-2" v-if="path.isdefault">默认</view>
					</view>
					<view class="font">{{path.path}}{{path.detailPath}}</view>
				</template>
				<template v-else>
					<view class="font-weight font-md d-flex a-center font-lg">请选择收货地址</view>
				</template>
			</view>
			<view class="iconfont icon-you ml-auto"></view>
		</view>
		<view style="border-top-left-radius: 25rpx;border-top-right-radius: 25rpx;margin-top: -25rpx;overflow: hidden;">
			<view class="bg-white">
				<uni-list-item showArrow>
					<view class="d-flex a-center">
						<image style="width: 100rpx;height: 100rpx;" class="rounded mr-2" src="/static/images/demo/cate_02.png"></image>
						<image style="width: 100rpx;height: 100rpx;" class="rounded mr-2" src="/static/images/demo/cate_05.png"></image>
						<image style="width: 100rpx;height: 100rpx;" class="rounded mr-2" src="/static/images/demo/cate_07.png"></image>
					</view>
					<view slot="rightContent">共3件</view>
				</uni-list-item>
				<uni-list-item title="商品总价" >
					<view slot="rightContent"><text class=" a-self-start font-md ">￥20.00</text></view>
				</uni-list-item>
				<uni-list-item title="运费" ><view slot="rightContent">包邮</view></uni-list-item>
				<uni-list-item title="优惠券" @click="openCoupon">
					<view slot="rightContent" >
						<text>无可用</text>
						<text></text>
					</view>
				</uni-list-item>
				<uni-list-item >
					<text class="main-text-color">小计</text>
					<view slot="rightContent"><text class=" a-self-start font-md main-text-color">￥20.00</text></price></view>
				</uni-list-item>
				<divider></divider>
				<uni-list-item @click="openOrderInvoice" title="发票" extraWidth="40%"><view slot="rightContent">电子发票-个人</view></uni-list-item>
			</view>
		</view>
		
			<view class="position-fixed d-flex a-center j-end border bottom-0 left-0 right-0 bg-white p-2 font-md">
					合计:
					<view class="ml-2">
						<text class=" a-self-start font-md main-text-color">￥20.00</text>
					</view>
			       <view @click="openPayMethods" class="ml-2 px-2 py-1 text-white font-md main-bg-color" hover-class="main-bg-hover-color" style="border-radius: 80rpx;">去支付</view>
		   </view>
	</view>
</template>

<script>
	import {mapGetters} from "vuex"
	import uniListItem from "@/components/uni-ui/uni-list-item/uni-list-item.vue"
export default {
	components:{
		uniListItem
	},
	data() {
		return {
			path:false
		};
	},
	onLoad() {
		if(this.defaultPath.length){
			this.path = this.defaultPath[0]
		}
		// 开启监听选择收货地址事件
		uni.$on('choosePath',(res)=>{
			// console.log('接收到参数',res)
			this.path = res
		})
	},
	onUnload() {
		// 关闭监听选择收货地址事件
		uni.$off('choosePath',(e)=>{
			console.log('关闭监听选择收货地址')
		})
	},
	computed:{
		...mapGetters(['defaultPath']),
	},
	methods: {
		// 获取收货地址
		openPathList(){
			uni.navigateTo({
				url:"../user-path-list/user-path-list?type=choose"
			})
		},
		// 跳转到电子发票页
		openOrderInvoice(){
			uni.navigateTo({
				url:"../order-invoice/order-invoice"
			})
		},
		// 去支付
		openPayMethods(){
			uni.navigateTo({
				url:"../pay-methods/pay-methods"
			})
		},
		// 选择优惠券
		openCoupon(){
			uni.navigateTo({
				url:"../order-coupon/order-coupon"
			})
		}
	}
};
</script>

<style >
	
</style>
