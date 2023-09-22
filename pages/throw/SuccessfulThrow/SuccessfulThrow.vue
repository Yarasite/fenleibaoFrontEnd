<template>
	<view class="content">
		<div class="text">
			</br>
			您已成功投放 {{ selectorArray[selectorIndex] }}  {{ weight }} kg<br>
			</br>
			您获得了 XX 绿色币<br>
			感谢您为垃圾分类作出的努力<br>
		</div>
		<div class="button1">
			<button class="again"@click="handleThrowAgain">继续投放</button>
			<button class="back"@click="handleBack">返回首页</button>
		</div>
	</view>
</template>

<script>
	import '@/style/success.css'
	export default {
		data() {
			    return {
			      selectorArray: ['可回收垃圾', '有害垃圾', '厨余垃圾', '其他垃圾'],
			      selectorIndex: 0,
			      weight: 0
			    };
			  },
			onLoad(options) {
			// 在页面加载时获取传递的 weight 和 selectorIndex 数据
			const selectorIndex = options.selectorIndex;
			if (options.weight) {
			  this.weight = options.weight;
			}
			if (options.selectorIndex) {
			  this.selectorIndex = options.selectorIndex;
			}
		},
		methods: {
			handleThrowAgain() {
				uni.navigateTo({
					url: "/pages/throw/Throw"
				})
			},
			handleBack() {
				uni.switchTab({
					url: "/pages/tabbar/tabbar-1/tabbar-1" // 跳转到主页面
				})
			}
		}
	}
</script>

<style>
.content {
	text-align: center;
}

.text {
  margin-top: 10upx; /* 上边距设为20%视窗高度，使文本垂直居中 */
}

.button1 {
	position: absolute;
	bottom: 0;
	width: 100%;
}

.again,
.back {
  color: #1b1b1b; /* 设置按钮文字颜色为黑色 */
}

.again {
	background-color: rgb(191, 191, 61);
}

.back {
	background-color: rgb(64, 149, 229);
}
</style>