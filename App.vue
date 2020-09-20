<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
			// 初始化登录状态 （退出app后再次进入登录状态还在）
			  this.$store.commit('initUser')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* 官方ui库 */
	@import "/common/uni.css";
	/* 第三方动画库 */
	@import "/common/animate.css";
	/* 自定义图标库 */
	@import "/common/icon.css";
	/* 自定义样式库 */
	@import "./common/free.css";
	/* 全局样式 */
	@import "./common/common.css";
	/* 解决小程序和app滚动条的问题 */ /* #ifdef MP-WEIXIN || APP-PLUS */
::-webkit-scrollbar {
	display: none;
} /* #endif */ /* 解决H5 的问题 */ /* #ifdef H5 */
uni-scroll-view .uni-scroll-view::-webkit-scrollbar {
	/* 隐藏滚动条，但依旧具备可以滚动的功能 */
	display: none;
} /* #endif */
</style>
