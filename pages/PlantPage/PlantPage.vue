<template>
	<div id="container">
		<div>
			XX垃圾处理厂
		</div>
		<div class="select">
			<h4>请选择要收入的垃圾种类:</h4>
			<div id="type">
				<picker mode="selector" :range="selectorArray" @change="onPickerChange">
					<view class="picker">
						{{ selectorArray[selectorIndex] }}
					</view>
				</picker>
			</div>
		</div>
		<div class="box">
			<FInput
			title="收到垃圾重量:" 
			placeholder="输入数字" 
			unit="t"
			v-model="weight">
			</FInput>
		</div>
		<div class="button">
			<button class="confirm" @click="handleConfirmThrow">确认收到</button>
			<button class="cancel" @click="handleGoBack">退出登录</button>
		</div>
	</div>
</template>

<script>
	import FInput from "@/components/FInput.vue"
	export default {
		components:{FInput},
		data() {
			return {
				selectorArray: ['可回收垃圾', '有害垃圾', '厨余垃圾', '其他垃圾'], // 下拉框选项数组
				selectorIndex: 0 ,// 默认选中的选项索引
				weight: '' //投放垃圾的重量
			};
		},
		methods: {
			onPickerChange(event) {
				// 获取选中的选项索引
				this.selectorIndex = event.detail.value;
				// 执行相关逻辑操作
				console.log('选中的选项：', this.selectorArray[this.selectorIndex]);
			},
			handleGoBack() {
				uni.navigateTo({
					url: "/pages/loginregister/loginregister/loginregister",
				}); 
			},
			handleConfirmThrow() {
				const selectorIndex = this.selectorIndex;
				const weight = this.weight; 
				uni.request({
				      url:'',
				     data:{
				       type: this.selectorIndex, //投放垃圾的类型
				        weight: this.weight
				      },
				      method: 'POST',
				       success() {
				        uni.showToast({
				        	title:'post请求发送成功',
				        	mask:true,
				        	icon:'none',
				        	duration:3000
				        })
				        uni.navigateTo({
				         // url: "/pages/throw/SuccessfulThrow/SuccessfulThrow?weight=" + this.weight + "&selectorIndex=" + this.selectorIndex
							url:"/pages/PlantPage/SucccessfulReceive/SucccessfulReceive?selectorIndex=" + selectorIndex + "&weight=" + weight,
				   });
				 }
			   });
				
			}
		}
	};
</script>

<style>
	#container {
		text-align: center;
	}

.select{
	margin-top: 150upx;
}
	.box {
		padding-top: 50upx;
	}
	.picker {
		display: inline-block;
		background-color: #fff;
		width: 100%;
		border: 1upx solid rgb(203, 206, 197);
		line-height: 40upx;
		border-radius: 10upx 10upx;
	}

	#type {
		display: block;
		width: 40%;
		margin-left: 30%;
		height: 30upx;
		margin-top: 10upx;
		border-color: rgb(203, 206, 197);
		color: rgb(151, 136, 151);
		font-size: 16upx;
	}

	#weight {
		display: inline-block;
		width: 40%;
		height: 30upx;
		margin-top: 15upx;
		border: 1upx solid rgb(203, 206, 197);
		color: rgb(151, 136, 151);
		font-size: 16upx;
		background-color: #fff;
		text-align: left;
		text-indent: 5upx;
	}

	.t {
		display: inline-block;
		vertical-align: top;
		margin-top: 15upx;
		height: 30upx;
		line-height: 30upx;
		margin-left: 2upx;
	}

	.button {
		position: absolute;
		bottom: 0;
		width: 100%;
	}

	.confirm {
		background-color: rgb(191, 191, 61);
	}

	.cancel {
		background-color: rgb(64, 149, 229);
	}
</style>