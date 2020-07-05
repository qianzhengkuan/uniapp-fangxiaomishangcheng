<template>
	
		<view class="row">
			<view class=" px-2 mb-2 text-center" v-for="(item,index) in label.list" :key="index">
				<view class="px-2 py-1 bg-light-secondary font-md  rounded" 
				:class="label.selected ===index ? 'radio-active':'bg-light-secondary' "
				@click="changeRadio(index)"
				>{{item.name}}</view></view>
		</view>

</template>

<script>
	export default{
		props:{
			label:Object
		},
		methods:{
			changeRadio(index){
				this.$emit('update:selected',index)
			}
		}
	}
</script>

<style scoped>
	.radio-active {
		background: #fce0d5 !important;
		color: #eb7320 !important;
		border-color: #eb7320 !important;
		border: 1rpx solid #eb7320 !important ;
	}
	
</style>
