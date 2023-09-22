<template>
	<view class="content">
		<div class="text1">
			请选择用户类型：
		</div>
		<div class="select">
			<picker   mode="selector" :range="selectorArray" @change="onPickerChange">
				<view class="picker">
					{{ selectorArray[selectorIndex] }}
				</view>
			</picker>
		</div>
		<div class="text2">
			手机号：
		</div>
		<div class="input-container">
			<input type="text" class="input1" v-model="user">
		</div>
		<div class="text3">
			密码：
		</div>
		<div class="input-container">
			<input type="safe-password" class="input1" v-model="pwd">
		</div>
		<br>
		<div class="lbutton">
			<button class="lbutton1" @click="handleLogin">登录</button>
			<button class="lbutton2" @click="handleBack">返回</button>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				selectorArray: ['普通用户', '垃圾运输车', '垃圾处理厂'], // 下拉框选项数组
				selectorIndex: 0, // 默认选中的选项索引
				user:'', //用户名
				pwd:'', //密码
			};
		},
		onLoad() {
		    uni.hideBackHome();
		  },
		methods: {
			onPickerChange(event) {
				// 获取选中的选项索引
				this.selectorIndex = event.detail.value;
				// 执行相关逻辑操作
				console.log('选中的选项：', this.selectorArray[this.selectorIndex]);
			},
			handleLogin() {
				// 处理登录按钮点击事件的逻辑
				switch (this.selectorIndex) {
				        case 0:
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
				          		
				          	    uni.switchTab({
				          			url: "/pages/tabbar/tabbar-1/tabbar-1" // 跳转到主页面
				          		});   
				          	},
				          	fail: (error) => {
				          		uni.showToast({
				          			title:'post请求发送失败',
				          			mask:true,
				          			icon:'none',
				          			duration:3000
				          		})
				          		uni.switchTab({
				          			url: "/pages/tabbar/tabbar-1/tabbar-1" // 跳转到主页面
				          		});   
				          	}
				          })
				          break;
				        case 1:
				          uni.navigateTo({
				            url: "/pages/CarPage/CarPage" // 跳转到页面2
				          });
				          break;
				        case 2:
				          uni.navigateTo({
				            url: "/pages/PlantPage/PlantPage" // 跳转到页面3
				          });
				          break;
				        default:
				          // 默认情况
				          break;}
				
				
				
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
	.lbutton {
		display: flex;
		justify-content: center;
		align-items: center;
		margin-bottom: 10px;
	}
	.lbutton1{
		background-color: rgba(129, 179, 55, 1);
		  color: rgb(255, 255, 255, 1);
		  border: none;
		  margin-right: 10upx; /* 添加间距 */
	}
	
	.lbutton2{
		background-color: rgba(233, 157, 66, 1);
		  color: rgb(255, 255, 255, 1);
		  border: none;
	}
	

</style>