<template>
	<view class="page">
		<leftBtns></leftBtns>
		<view class="right">
			<h3>登录页</h3>
			<view class="user">
				<el-input v-model="userNO" placeholder="请输入账号"></el-input>
			</view>
			<view class="user">
				<el-input v-model="password" placeholder="请输入密码" show-password></el-input>
			</view>
			<el-button type="primary" @click="goLogin">登录</el-button>
		</view>
	</view>
</template>

<script>
	import leftBtns from '../../components/leftBtns.vue'
	export default {
		components: {
			leftBtns
		},
		data() {
			return {
				userNO: '', //账号
				password: '' //密码
			}
		},
		methods: {
			goLogin() {
				console.log(this.userNO, this.password)
				axios.post('http://127.0.0.1:8060/web/login', {
						'login': this.userNO,
						'password': this.password,
					}, {}).then(res => {
						this.tableData = res.data
						console.log(res)
					})
					.catch(res => {
						// console.log(res.data)
					})
			}
		}
	}
</script>

<style>
	.page {
		display: flex;
	}
	.right {
		flex: 1;
		background-color: teal;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}
	.user {
		width: 50%;
		margin: 10px 0;
	}
</style>