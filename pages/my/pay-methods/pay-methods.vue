<template>
	<view>
		<view class="d-flex flex-column a-center j-center">
			<text class="text-light-muted font-md mt-5">支付金额</text>
			<text class=" font-lg main-text-color  mb-5">￥20.00</text>
		</view>
		<label>
			<view class="px-5">
				<uni-list-item :showArrow="false" leftIcon="icon-zhifubao text-primary" title="支付宝支付" showExtraIcon leftIconStyle="font-size:60rpx" note="推荐使用支付宝支付">
					<radio slot="right" value="1" color="#FD6801" />
				</uni-list-item>
			</view>
		</label>
		<label>
			<view class="px-5">
				<uni-list-item :showArrow="false" leftIcon="icon-weixinzhifu text-success" title="微信支付" showExtraIcon leftIconStyle="font-size:60rpx">
					<radio slot="right" value="2" color="#FD6801" />
				</uni-list-item>
			</view>
		</label>

		<view @click="submit" class="rounded text-white font-md  py-2 mt-5 text-center main-bg-color" style="width: 85%; margin: auto;margin-top: 50rpx;"  hover-class="main-bg-hover-color">确认支付</view>
	</view>
</template>

<script>
import uniListItem from '@/components/uni-ui/uni-list-item/uni-list-item.vue';
export default {
	components: {
		uniListItem
	},
	data() {
		return {};
	},
	methods: {
		submit(){
			uni.navigateTo({
				url:"../pay-result/pay-result"
			})
		}
	}
};
</script>

<style></style>
