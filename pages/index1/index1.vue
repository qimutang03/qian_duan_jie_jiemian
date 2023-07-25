<template>
	<view class="page">
		<leftBtns></leftBtns>
		<view class="right">
			<view class="box">
				<view class="type">
					<text>type:</text>
					<text class="content">{{typeName}}</text>
					<el-dropdown @command="handleCommand">
						<span class="el-dropdown-link">
							<i class="el-icon-arrow-down el-icon--right"></i>
						</span>
						<el-dropdown-menu slot="dropdown">
							<el-dropdown-item command="a">黄金糕</el-dropdown-item>
							<el-dropdown-item command="b">狮子头</el-dropdown-item>
							<el-dropdown-item command="c">螺蛳粉</el-dropdown-item>
							<el-dropdown-item command="d">双皮奶</el-dropdown-item>
						</el-dropdown-menu>
					</el-dropdown>
				</view>
				<view class="type">
					<text>conpany:</text>
					<text class="content">{{conpanyName}}</text>
					<el-dropdown @command="handleCommand1">
						<span class="el-dropdown-link">
							<i class="el-icon-arrow-down el-icon--right"></i>
						</span>
						<el-dropdown-menu slot="dropdown">
							<el-dropdown-item command="a">黄金糕</el-dropdown-item>
							<el-dropdown-item command="b">狮子头</el-dropdown-item>
							<el-dropdown-item command="c">螺蛳粉</el-dropdown-item>
							<el-dropdown-item command="d">双皮奶</el-dropdown-item>
						</el-dropdown-menu>
					</el-dropdown>
				</view>
				<view class="type">
					<text>Date:</text>
					<text class="content">{{dateyName}}</text>
					<el-dropdown @command="handleCommand2">
						<span class="el-dropdown-link">
							<i class="el-icon-arrow-down el-icon--right"></i>
						</span>
						<el-dropdown-menu slot="dropdown">
							<el-dropdown-item command="a">黄金糕</el-dropdown-item>
							<el-dropdown-item command="b">狮子头</el-dropdown-item>
							<el-dropdown-item command="c">螺蛳粉</el-dropdown-item>
							<el-dropdown-item command="d">双皮奶</el-dropdown-item>
						</el-dropdown-menu>
					</el-dropdown>
				</view>
			</view>
			<el-tabs v-model="activeName" type="card" @tab-click="handleClick">
				<el-tab-pane label="用户管理" name="first">
					<el-table stripe="stripe" ref="multipleTable" :data="tableData" tooltip-effect="dark" style="width: 100%"
						@selection-change="handleSelectionChange">
						<el-table-column prop="index" label="#" width="40">
						</el-table-column>
						<el-table-column type="selection" width="55">
						</el-table-column>
						<el-table-column prop="name" label="product Name" width="150">
						</el-table-column>
						<el-table-column prop="date" label="compary" width="120">
						</el-table-column>
						<el-table-column prop="address" label="Client" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="cardBoard" label="card board" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="numberBoxse" label="Box code" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="boxCode" label="number Boxse" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="cardBoardQuantity" label="card Board Quantity" show-overflow-tooltip>
						</el-table-column>
					</el-table>
				</el-tab-pane>
				<el-tab-pane label="配置管理" name="second">配置管理</el-tab-pane>
				<el-tab-pane label="角色管理" name="third">角色管理</el-tab-pane>
				<el-tab-pane label="定时任务补偿" name="fourth">定时任务补偿</el-tab-pane>
			</el-tabs>
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
				typeName: '',
				conpanyName: '',
				dateyName: '',
				activeName: 'first',
				dropdown: {
					a: '黄金糕',
					b: '狮子头',
					c: '螺蛳粉',
					d: '双皮奶'
				},
				stripe: true,
				tableData: [{
					index: '1',
					date: '2016-05-03',
					name: '米酒',
					address: '上海市普陀区金沙江路 1518 弄dddddddddddddddddd',
					cardBoard: 'ddddddddd',
					numberBoxse: 'aaaaaa',
					boxCode: 'qqqqq',
					cardBoardQuantity: 'ggggggg'
				}, {
					index: '2',
					date: '2016-05-02',
					name: '二锅头',
					address: '上海市普陀区金沙江路 1518 弄',
					cardBoard: 'ddddddddd',
					numberBoxse: 'aaaaaa',
					boxCode: 'qqqqq',
					cardBoardQuantity: 'ggggggg'
				}, {
					index: '3',
					date: '2016-05-04',
					name: '王老吉',
					address: '上海市普陀区金沙江路 1518 弄',
					cardBoard: 'ddddddddd',
					numberBoxse: 'aaaaaa',
					boxCode: 'qqqqq',
					cardBoardQuantity: 'ggggggg'
				}, {
					index: '4',
					date: '2016-05-01',
					name: '龟苓膏',
					address: '上海市普陀区金沙江路 1518 弄',
					cardBoard: 'ddddddddd',
					numberBoxse: 'aaaaaa',
					boxCode: 'qqqqq',
					cardBoardQuantity: 'ggggggg'
				}, {
					index: '5',
					date: '2016-05-08',
					name: '加多宝',
					address: '上海市普陀区金沙江路 1518 弄',
					cardBoard: 'ddddddddd',
					numberBoxse: 'aaaaaa',
					boxCode: 'qqqqq',
					cardBoardQuantity: 'ggggggg'
				}, {
					index: '6',
					date: '2016-05-06',
					name: '百威',
					address: '上海市普陀区金沙江路 1518 弄',
					cardBoard: 'ddddddddd',
					numberBoxse: 'aaaaaa',
					boxCode: 'qqqqq',
					cardBoardQuantity: 'ggggggg'
				}, {
					index: '7',
					date: '2016-05-07',
					name: '嘉士伯',
					address: '上海市普陀区金沙江路 1518 弄',
					cardBoard: 'ddddddddd',
					numberBoxse: 'aaaaaa',
					boxCode: 'qqqqq',
					cardBoardQuantity: 'ggggggg'
				}],
				multipleSelection: []
			}
		},
		methods: {
			handleCommand(command) {
				console.log(command)
				if (this.dropdown[command]) {
					this.typeName = this.dropdown[command]
				}
			},
			handleCommand1(command) {
				console.log(command)
				if (this.dropdown[command]) {
					this.conpanyName = this.dropdown[command]
				}
			},
			handleCommand2(command) {
				console.log(command)
				if (this.dropdown[command]) {
					this.dateyName = this.dropdown[command]
				}
			},
			handleClick(tab, event) {
				console.log(tab, event);
			},
			handleSelectionChange(val) {
				this.multipleSelection = val;
			},
			goPage(url) {
				uni.navigateTo({
					url
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
		/* display: flex; */
	}
	.el-button--success {
		width: 120px;
	}
	.box {
		flex: 1;
		display: flex;
	}

	.type {
		vertical-align: bottom;
		margin: 15px;
	}

	.content {
		display: inline-block;
		width: 50px;
		border-bottom: 1px solid #606266;
		margin: 0 10px;
	}
</style>