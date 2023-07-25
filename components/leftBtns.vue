<template>
	<view>
		<view class="leftBtns">
			<view class="btn"><el-button size="medium" type="success" @click="goPage('/pages/login/login')">跳转登录页</el-button></view>
			<view  class="btn"><el-button size="medium" type="success" @click="goPage('/pages/index/index')">跳转index</el-button></view>
			<view  class="btn"><el-button size="medium" type="success" @click="goPage('/pages/index1/index1')">跳转index1</el-button></view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "leftBtns",
		data() {
			return {

			};
		},
		methods: {
			goPage(url) {
				uni.navigateTo({
					url
				})
			}
		}
	}
</script>

<style>
	.leftBtns {
		width: 150px;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.el-button--success {
		width: 120px;
		margin: 5px;
	}
</style>