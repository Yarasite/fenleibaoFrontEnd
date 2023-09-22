<template>

	<view class="content">
		<div class="button">
			<button @click="handleAccountInfo">账户信息</button>
		</div>
		<div class="button">
			<button @click="handleExchange">兑换绿色币</button>
		</div>
		<div class="button">
			<button @click="handleHelp">帮助与反馈</button>
		</div>
		<div class="button">
			<button @click="handleSetting">设置</button>
		</div>
	</view>

</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			handleAccountInfo() {
				// 处理按钮点击事件的逻辑
				uni.navigateTo({
					url: "/pages/tabbar/tabbar-5/AccountInformation/AccountInformation" // 跳转到登录页面
				});
			},
			handleExchange() {
				// 处理按钮点击事件的逻辑
				uni.navigateTo({
					url: "/pages/tabbar/tabbar-5/ExchangeCoin/ExchangeCoin" // 跳转到登录页面
				});
			},
			handleHelp() {
				// 处理按钮点击事件的逻辑
				uni.navigateTo({
					url: "/pages/tabbar/tabbar-5/HelpAndFeedBack/HelpAndFeedBack" // 跳转到登录页面
				});
			},
			handleSetting() {
				// 处理按钮点击事件的逻辑
				uni.navigateTo({
					url: "/pages/tabbar/tabbar-5/setting/setting" // 跳转到登录页面
				});
			}
		}
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
		margin-top: 0upx;
	}

	.button button{
		background-color: rgba(86,119,34, 0.7);
		color: rgba(0, 0, 0, 1);
		border: none;
	}
</style>