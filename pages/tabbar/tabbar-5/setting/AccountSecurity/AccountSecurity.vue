<template>

	<view class="content">
		<div class="button">
			<button @click="handleChangePassword">修改密码</button>
		</div>
		<div class="button">
			<button @click="handleAccountCancellation">注销账号</button>
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
			handleChangePassword() {
				// 处理按钮点击事件的逻辑
			},
			handleAccountCancellation() {
				// 处理按钮点击事件的逻辑
			},
			handleBack() {
				// 处理按钮点击事件的逻辑
				uni.navigateBack();
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
		background-color: rgba(86,119,34,0.7);
		color: rgba(0, 0, 0, 1);
		border: none;
	}

	.backbutton {
		position: absolute;
		bottom: 0;
		width: 100%;
	}
</style>