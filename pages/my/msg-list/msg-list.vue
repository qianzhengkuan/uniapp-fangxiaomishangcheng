<template>
	<view class="p-2">
		<view class="mb-2 p-2 bg-white rounded" hover-class="bg-light"
		v-for="(item,index) in list" :key="index"
		@click="open(item)">
			<view class="text-dark font-md">{{item.title}}</view>
			<view class="font text-light-muted">
				{{item.desc}}
			</view>
			<view class="font text-light-muted">{{item.create_time}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list:[
					{
						title:"热门手机正式开售啦",
						desc:"性能高价格低",
						create_time:"9月份"
					},
					{
						title:"热门手机正式开售啦",
						desc:"性能高价格低",
						create_time:"9月份"
					}
				]
			}
		},
		methods: {
			open(item){
				uni.navigateTo({
					url: '../msg-detail/msg-detail?detail='+JSON.stringify(item),
				});
			}
		}
	}
</script>

<style>
page{
	background-color: #EEEEEE;
}
</style>
