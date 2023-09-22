<!-- 自定义组件 FenLeiBaoInput, 简称FInput
 共3个属性:
 title:标题,显示在输入框上方
 placeholder:默认显示内容
 unit:数值的单位,可以为空-->
<template>
	<div class="box">
		<h4>{{ title }}</h4>
		<input type="digit" :placeholder="placeholder" v-on:input="inputFn">
		<span>{{ unit }}</span>
	</div>
</template>

<script>
	export default{
		name:'FInput',
		props:['title', 'placeholder', 'unit'],
		methods: {
		    inputFn(e) {
		      this.$emit("input", e.target.value);
		    },
		},
	}
</script>

<style>
	.box {
		padding-top: 100upx;
	}
	.box > input {
		display: inline-block;
		width: 40%;
		height: 40upx;
		margin-top: 15upx;
		line-height: 40upx;
		border-radius: 10upx 10upx;
		border: 1upx solid rgb(203, 206, 197);
		color: rgb(151, 136, 151);
		font-size: 16upx;
		background-color: #fff;
		text-align: left;
		text-indent: 10upx;
	}
	
	.box > span {
		display: inline-block;
		vertical-align: top;
		margin-top: 15upx;
		height: 40upx;
		line-height: 40upx;
		margin-left: 2upx;
	}
</style>