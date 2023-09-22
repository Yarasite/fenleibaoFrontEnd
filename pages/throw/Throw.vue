<template>
	<div id="container">
		<div class="select">
			<h4>请选择要投放的垃圾种类:</h4>
			<div id="type">
				<picker mode="selector" :range="selectorArray" @change="onPickerChange">
					<view class="picker">
						{{ selectorArray[selectorIndex] }}
					</view>
				</picker>
			</div>
		</div>
		
		<FInput 
		title="请输入投入垃圾的重量:" 
		placeholder="单行输入" 
		unit="kg"
		v-model="weight"></FInput>
		<div class="button">
			<button class="confirm" @click="handleConfirmThrow">确认投放</button>
			<button class="cancel" @click="handleGoBack">返回</button>
		</div>
	</div>
</template>

<script scoped>
	import FInput from '@/components/FInput.vue';
	export default {
		components: {
			FInput
		},
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
				uni.switchTab({
					url: "/pages/tabbar/tabbar-1/tabbar-1" // 跳转到主页面
				})
			},
			handleConfirmThrow() {
				console.log(this.weight)
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
							url: '/pages/throw/SuccessfulThrow/SuccessfulThrow?selectorIndex=' + selectorIndex + "&weight=" + weight,
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
	padding-top: 150upx;
}

.picker{
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