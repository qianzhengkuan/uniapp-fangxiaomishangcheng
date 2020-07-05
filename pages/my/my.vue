<template>
	<view>
		<!-- 头部 -->
		<view class="position-relative d-flex a-center animated fadeIn faster" style="height: 320rpx;">
			<!-- 解决首次加载页面白屏的问题 -->
			<loading-plus v-if="beforeReady"></loading-plus>
			<!-- 消息列表 -->

			<view @click="navigate('msg-list')" class="iconfont icon-xiaoxi position-absolute text-white" style="font-size: 50rpx;top: 75rpx;right: 20rpx;z-index: 100;"></view>

			<image src="../../static/images/bg.jpg" style="height: 320rpx;width: 100%;"></image>

			<view class="d-flex a-center position-absolute left-0 right-0" style="bottom: 50rpx;">
				<image :src="loginStatus ? userInfo.avatar : '/static/images/demo/demo6.jpg'" style="height: 145rpx;width: 145rpx;border: 5rpx solid;" class="rounded-circle border-light ml-4"></image>
				<view class="ml-2 text-white font-md" @click="openLogin">{{ loginStatus ? userInfo.nickname : '登录/注册' }}</view>
				<view
					class="d-flex a-center j-center a-self-end ml-auto px-2"
					style="height: 70rpx;background: #FFD43F;color: #CC4A00;border-top-left-radius: 40rpx;border-bottom-left-radius: 40rpx;"
				>
					<view class="line-h iconfont icon-huangguan mr-1"></view>
					会员积分 0.00
				</view>
			</view>
		</view>
		<!--我的订单 -->
		<card>
			<view slot="title" class="d-flex a-center j-sb w-100">
				<text class="font-md font-weight">我的订单</text>
				<view class="text-secondary font ml-auto" @click="navigate('order')">
					全部订单
					<text class="iconfont icon-you font"></text>
				</view>
			</view>
			<view class="d-flex a-center">
				<view class="flex-1 d-flex flex-column a-center j-center py-3" hover-class="bg-light-secondary" v-for="(item, index) in orders" :key="index">
					<view class="iconfont font-lg line-h" :class="item.icon"></view>
					<view>{{ item.name }}</view>
				</view>
			</view>
		</card>
		<!-- 分割线 -->
		<divider></divider>
		<view class=""><image src="../../static/images/demo/demo4.jpg" style="width: 100%; height: 300rpx;" mode="widthFix"></image></view>
		<divider></divider>
		<view class="">
			<uni-list-item showExtraIcon leftIconStyle="color:#FDBF2E;" leftIcon="icon-VIP" title="小米会员"></uni-list-item>
			<uni-list-item showExtraIcon leftIconStyle="color:#FCBE2D;" leftIcon="icon-huangguan" title="会员中心"></uni-list-item>
			<uni-list-item showExtraIcon leftIconStyle="color:#FA6C5E;" leftIcon="icon-service" title="服务中心"></uni-list-item>
			<uni-list-item showExtraIcon leftIconStyle="color:#FE8B42;" leftIcon="icon-home" title="小米之家"></uni-list-item>
			<uni-list-item showExtraIcon leftIconStyle="color:#9ED45A;" leftIcon="icon-gengduo" title="更多功能"></uni-list-item>
			<divider></divider>
			<uni-list-item @click="navigate('user-set')" showExtraIcon leftIconStyle="color:#808C98;" leftIcon="icon-icon_set_up" title="更多设置"></uni-list-item>
		</view>
	</view>
</template>

<script>
import loading from '@/common/mixin/loading.js';
import card from '@/components/common/card.vue';
import uniListItem from '@/components/uni-ui/uni-list-item/uni-list-item.vue';
import { mapState } from 'vuex';
export default {
	mixins: [loading],
	components: {
		card,
		uniListItem
	},
	data() {
		return {
			orders: [
				{
					name: '待付款',
					icon: 'icon-wallet_icon',
					index: 1
				},
				{
					name: '待收货',
					icon: 'icon-daishouhuo',
					index: 2
				},
				{
					name: '待评价',
					icon: 'icon-pinglun',
					index: 3
				},
				{
					name: '待退修',
					icon: 'icon-buoumaotubiao46'
				}
			]
		};
	},
	computed: {
		...mapState({
			loginStatus: state => state.user.loginStatus,
			userInfo: state => state.user.userInfo
		})
	},
	methods: {
		// 跳转页面
		navigate(path) {
			if (!path) return;
			// 先进行登录验证
			this.navigateTo({
				url: `./${path}/${path}`
			});
		},
		// 登录
		openLogin() {
			if (!this.loginStatus) {
				uni.navigateTo({
					url: '../login/login'
				});
			}
		}
	}
};
</script>

<style></style>
