<template>
	<view class="content">
		<div class="tree">
			<image src="../../../static/img/tree1.png" alt="树" mode="widthFix" @click="showRandomTip"></image>
			<div v-if="showTip" class="tip">{{ randomTip }}</div>
		</div>
		<div class="button">
			<button @click="handleThrow">投放垃圾</button>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showTip: false,
				tips: [
					"可回收物(再生资源)是指回收后经过再加工可以成为生产原料或者经过整理可以再利用的物品。",
					"狭义的厨余垃圾是有机垃圾的一种，分为熟厨余垃圾、生厨余垃圾，泛指家庭生活饮食中所需用的来源生料及成品(熟食)或残留物；广义的厨余垃圾还包括用过的筷子，食品的包装材料等",
					"有毒有害垃圾是指存有对人体健康有害的重金属、有毒的物质或者对环境造成现实危害或者潜在危害的废弃物。",
					"其他垃圾包括除可回收、有害、厨余几类垃圾之外难以回收的废弃物，通常根据垃圾特性采取焚烧或者填埋的方式处理",
					"常见可回收垃圾包括废纸类、塑料类、玻璃类、电子废弃物类、金属类、织物类",
					"常见厨余垃圾包括剩菜、剩饭、菜叶、果皮、蛋壳、茶渣、骨、贝壳等",
					"常见有害垃圾包括废药品、废杀虫剂、废消毒剂、废油漆、废溶剂、废矿物油、废化妆品、废胶片、废相纸、废荧光灯管、废温度计、废血压计、废充电电池、废扣子电池、碱性电池、锂电池、镍镉电池等。",
					"常见其他垃圾包括使用过的卫生纸、复写纸、传真纸、照片、离心纸、蜡纸、转印纸、塑料光面废纸、妇女用卫生巾、婴儿纸尿布、餐巾纸、烟蒂、陶瓷制品、衣服、鞋类、石棉瓦、白板、木质玩具、雨鞋、木质家具、橡胶制品、轮胎等",
				],
				randomTip: "",
			};
		},
		methods: {
			handleThrow() {
				uni.navigateTo({
					url: '/pages/throw/Throw'
				})
			},
			showRandomTip() {
				const randomIndex = Math.floor(Math.random() * this.tips.length);
				this.randomTip = this.tips[randomIndex];
				this.showTip = true;

				// 设置一段时间后隐藏提示
				setTimeout(() => {
					this.showTip = false;
				}, 6000); // 6秒后隐藏提示，可以根据需要调整时间
			},
		},
	}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
		margin-top: 0upx;
	}

	.tip {
		position: fixed;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		background-color: #66b2ff;
		padding: 10px;
	}

	.tree {
		display: flex;
		justify-content: center;
		/* 水平居中 */
		align-items: center;
		/* 垂直居中 */
		margin-top: 100upx;
	}

	.tree img {
		width: 600upx;
		/* 限制图片宽度 */
		height: 900upx;
		/* 限制图片高度 */
	}

	.button {
		position: absolute;
		width: 40%;
		bottom: 10%;
		left: 30%;
	}

	.button button {
		background-color: rgb(191, 191, 61);
	}
</style>