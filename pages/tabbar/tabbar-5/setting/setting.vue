<template>

	<view class="content">
		<div class="button">
			<button @click="handleAccountSecurity">账号与安全</button>
		</div>
		<div class="button">
			<button @click="handleLogOut">退出登录</button>
		</div>
		<div class="button">
			<button class="backbutton" @click="handleBack">返回</button>
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
			handleAccountSecurity() {
				// 处理按钮点击事件的逻辑
				uni.request({
					url:'',
					data:{},
					success() {
						alert('get请求发送成功')
					}
				})
				uni.navigateTo({
					url: "/pages/tabbar/tabbar-5/setting/AccountSecurity/AccountSecurity"
				})
			},
			handleLogOut() {
				// 处理按钮点击事件的逻辑
				uni.request({
					url:'',
					data:{},
					success() {
						alert('get请求发送成功')
					}
				})
				uni.navigateTo({
					url: "/pages/loginregister/loginregister/loginregister"
				})
			},
			handleBack() {
				// 处理按钮点击事件的逻辑
				uni.switchTab({
					url: "/pages/tabbar/tabbar-5/tabbar-5" // 跳转到主页面
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
		background-color: rgba(86, 119, 34, 0.7);
		color: rgba(0, 0, 0, 1);
		border: none;
	}

	.backbutton {
		position: absolute;
		bottom: 0;
		width: 100%;
	}
</style>