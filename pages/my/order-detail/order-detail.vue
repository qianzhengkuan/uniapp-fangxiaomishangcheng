<template>
	<view>
		<!-- 头部 -->
		<view class="main-bg-color text-white p-4 d-flex a-end j-sb" style="height: 300rpx;">
			<view class="mb-3">
				<view class="font-lg">卖家已发货</view>
				<view class="font">还差7天10时自动收货</view>
			</view>
			<view class="iconfont icon-daishouhuo line-h mb-3" style="font-size: 100rpx;"></view>
		</view>
		<!-- 收货信息 -->
		<view class="p-3 bg-white">
			<view class="text-light-muted font-md">
				<text class="font-lg text-dark mr-2">钱大剩</text>
				180709789898
			</view>
			<view class="text-light-muted font-md">地址</view>
		</view>
		<divider></divider>
		<!-- 商品列表 -->
		<view class="px-2">
			<block v-for="(item, index) in order_items" :key="index"><order-list-item :item="item" :index="index"></order-list-item></block>
		</view>
		<divider></divider>

		<uni-list-item>
			<text class="font-md text-light-muted">商品总价</text>
			<view slot="right" class="font-md text-light-muted"><text class="">$110.00</text></view>
		</uni-list-item>
		<uni-list-item>
			<text class="font-md text-light-muted">快递</text>
			<view slot="right" class="font-md text-light-muted">包邮</view>
		</uni-list-item>
		<uni-list-item>
			<text class="font-md text-light-muted">优惠券</text>
			<view slot="right" class="font-md text-light-muted"><text class="">$110.00</text></view>
		</uni-list-item>
		<uni-list-item>
			<text class="font-md main-text-color">实际付款</text>
			<view slot="right" class="font-md text-light-muted"><text class="main-text-color">$110.00</text></view>
		</uni-list-item>
		<divider></divider>

		<card headTitle="订单信息">
			<uni-list-item title="订单编号">
				<view slot="right" class="font-md text-light-muted">{{ no }}</view>
			</uni-list-item>
		</card>
		<card v-if="extra" headTitle="退款相关">
			<uni-list-item title="申请退款">
				<view slot="right" class="font-md text-light-muted">{{ extra.refund_reason }}</view>
			</uni-list-item>
		</card>
	</view>
</template>

<script>
import orderListItem from '@/components/order/order-list-item.vue';
import uniListItem from '@/components/uni-ui/uni-list-item/uni-list-item.vue';
import card from '@/components/common/card.vue';
export default {
	components: {
		orderListItem,
		uniListItem,
		card
	},
	data() {
		return {
			order_items: [
				{
					cover: '/static/images/demo/cate_02.png',
					title: '小米8',
					pprice: 1999.0,
					attrs: '金色 标配',
					num: 1
				},
				{
					cover: '/static/images/demo/cate_05.png',
					title: '小米8',
					pprice: 4999.0,
					attrs: '金色 标配',
					num: 1
				},
				{
					cover: '/static/images/demo/cate_07.png',
					title: '小米8',
					pprice: 3999.0,
					attrs: '金色 标配',
					num: 1
				}
			]
		};
	},
	methods: {}
};
</script>

<style></style>
