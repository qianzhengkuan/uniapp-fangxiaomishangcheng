<template>
	<view class="">
		<view class="card">
			<!-- 标题 -->
			<view v-if="showhead" class="p-2 main-border-color d-flex a-center j-sb" :class="getHeadClass">
				<slot name="title">
					<!--如果没值头部就隐藏 -->
					<text v-if="headTitle" class="font-md  " :class="headTitleWeight ? 'font-weight':''">{{ headTitle }}</text>
				</slot>
				<slot name="right"></slot>
			</view>
			<!-- body -->
			<view :class="getBodyClas">
				<image v-if="bodyCover" :src="bodyCover" mode="widthFix"></image>
				<!-- 放插槽 -->
				<slot />
			</view>
		</view>
	</view>
</template>

<script>
export default {
	props: {
		// 头部标题
		headTitle: String,
		// 封面图
		bodyCover: String,
		// 是否显示头部
		showhead: {
			type: Boolean,
			default: true
		},
		// 是否显示下边线
		headBorderBottom: {
			type: Boolean,
			default: true
		},
		// 是否给body加padding
		bodyPadding: {
			type: Boolean,
			default: false
		},
		// 标题是否加粗
		headTitleWeight:{
			type: Boolean,
			default: true
		}
	},
	computed: {
		getHeadClass() {
			let BorderBottom = this.headBorderBottom ? 'border-bottom' : '';
			return `${BorderBottom}`;
		},
		getBodyClas() {
			let padding = this.bodyPadding ? 'py-2' : '';
			return `${padding}`;
		}
	}
};
</script>

<style></style>
