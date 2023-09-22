<template>
	<view class="content">
		<div class="text1">
			请输入垃圾处理厂名称：
		</div>
		<div class="input-container">
			<input type="text" class="input1" v-model="user">
		</div>
		<br>
		<div class="text3">
			请输入可处理垃圾类型：
		</div>
		<div class="input-container">
			<input type="text" class="input1" v-model="pwd">
		</div>
		<br>
		<div class="rbutton">
			<button class="rbutton1" @click="handleRegister()">注册</button>
			<button class="rbutton2" @click="handleBack">返回</button>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				selectorArray: ['普通用户', '垃圾运输车', '垃圾处理厂'], // 下拉框选项数组
				selectorIndex: 0 ,// 默认选中的选项索引
				user: '',
				pwd: ''
			};
		},
		onLoad() {},
		methods: {
			onPickerChange(event) {
				// 获取选中的选项索引
				this.selectorIndex = event.detail.value;
				// 执行相关逻辑操作
				console.log('选中的选项：', this.selectorArray[this.selectorIndex]);
			},
			handleRegister() {
				// 处理注册按钮点击事件的逻辑
				
				uni.request({
					url:'',
					data:{
						type: this.selectorIndex, //用户类型
						user: this.user,
						pwd: this.pwd
					},
					method: 'POST',
					success: (res) => {

						uni.showToast({
							title:'post请求发送成功',
							mask:true,
							icon:'none',
							duration:3000
						})
					    uni.navigateTo({
							url: '/pages/loginregister/login/login' // 跳转到登录页面
						});
					},
					fail: (error) => {
						uni.showToast({
							title:'post请求发送失败',
							mask:true,
							icon:'none',
							duration:3000
						})
					}
				})
				
			},
			handleBack() {
				// 处理返回按钮点击事件的逻辑
				uni.navigateTo({
					url: "/pages/loginregister/loginregister/loginregister" // 跳转到上一页面
				});
			}
		}
	};
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
		margin-top: 150upx;
	}
	
	.picker{
		display: inline-block;
		background-color: #fff;
		width: 300upx;
		border: 1upx solid rgb(203, 206, 197);
		color: rgb(151, 136, 151);
		line-height: 60upx;
		margin-top: 20upx;
		border-radius: 10upx 10upx;
	}

	.input-container {
		display: flex;
		justify-content: center;
		/* 子元素水平居中 */
	}

	.input1 {
		width: 200px;
		/* 设置输入框宽度 */
		height: 20px;
		/* 设置输入框高度 */
		padding: 5px;
		/* 设置内边距 */
		font-size: 14px;
		/* 设置字体大小 */
		background-color: rgb(255, 255, 255);
	}

	.select,
	.text2 {
		margin-bottom: 50px;
		/* 设置文本之间的间隔 */
	}

	.text2,
	.text3 {
		margin-bottom: 10px;
		/* 设置文本之间的间隔 */
	}

	.input-container,
	.rbutton {
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.rbutton1{
		background-color: rgba(129, 179, 55, 1);
		  color: rgb(255, 255, 255, 1);
		  border: none;
		  margin-right: 10upx; /* 添加间距 */
	}
	
	.rbutton2{
		background-color: rgba(233, 157, 66, 1);
		  color: rgb(255, 255, 255, 1);
		  border: none;
	}
</style>