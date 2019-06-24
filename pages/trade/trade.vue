<template>
	<view v-if="userNiuRen" class="content">
		<uni-list>
			<uni-list-item @tap="tapswitch" title="长城证券" note="点击切换主账户" thumb="/static/icons/greatwall.jpg"></uni-list-item>
		</uni-list>

		<view class="assetArea">
			<view class="assetItem">
				<text>总资产</text>
				<text>10000.00</text>
			</view>
			<view class="assetItem">
				<text>浮动盈亏</text>
				<text class="profit">10000.00</text>
			</view>
			<view class="assetItem">
				<text>总市值</text>
				<text>10000.00</text>
			</view>
			<view class="assetItem">
				<text>当日盈亏</text>
				<text class="profit">10000.00</text>
			</view>
		</view>

		<view class="handleArea">
			<view class="handleItem" data-tab=0 @tap="handleTrade">
				<image class="handle-icon" src="/static/icons/buy.png" mode="scaleToFill"></image>
				<text>买入</text>
			</view>
			<view class="handleItem" data-tab=1 @tap="handleTrade">
				<image class="handle-icon" src="/static/icons/sell.png"></image>
				<text>卖出</text>
			</view>
			<view class="handleItem" data-tab=2 @tap="handleTrade">
				<image class="handle-icon" src="/static/icons/che2.png"></image>
				<text>撤单</text>
			</view>
			<view class="handleItem" data-tab=3 @tap="handleTrade">
				<image class="handle-icon" src="/static/icons/hold.png"></image>
				<text>持仓</text>
			</view>
		</view>
		<view class="otherList">
			<uni-list>
				<uni-list-item @click="choose1" note="当前子账户为00001" title="切换子账户"></uni-list-item>
				<uni-list-item @click="choose2" title="交易规则"></uni-list-item>
				<uni-list-item @tap="choose3" title="意见反馈"></uni-list-item>
			</uni-list>
		</view>
	</view>

	<view v-else>
		<view class="container">
			<view class="accountArea">
				<view v-for="(item,index) in data" class="subAccountArea">
					<view class="s-head">
						<image class="avatar" src="/static/icons/greatwall.jpg" mode="scaleToFill"></image>
						<text class="title">我的策略{{item}}</text>
						<view @click="chooseStg(index)" class="head-arrow">
							<uni-icon type="arrowright" size="20"></uni-icon>
						</view>
					</view>
					<view class="account-handle">
						<button>启用</button>
						<button>暂停</button>
						<button>关闭</button>
					</view>
				</view>
			</view>

		</view>
		<view class="b-area" />
		<uni-popup msg="1111" :show="true" type="middle">
			<view class="title">选择牛人</view>
			<view class="tishi">*您最少要选择5-10个牛人</view>
			<view class="warp">
				<view class="box">
					<t-table @change="change">
						<t-tr>
							<t-th>选择</t-th>
							<t-th>姓名</t-th>
							<t-th>排名</t-th>
							<t-th>收益率</t-th>
							<t-th>回撤</t-th>
							<t-th>胜率</t-th>
						</t-tr>
						<t-tr v-for="items in niuren" :key="items.id">
							<t-td>
								<checkbox style="transform:scale(0.5)"></checkbox>
							</t-td>
							<t-td>{{items.name}}</t-td>
							<t-td>{{items.paiming}}</t-td>
							<t-td>{{items.shouyilv}}</t-td>
							<t-td>{{items.huiche}}</t-td>
							<t-td>{{items.shenglv}}</t-td>
						</t-tr>
					</t-table>
					<view class="fanye">
						<uni-pagination show-icon="true" total="50" current="1">
						</uni-pagination>
					</view>
				</view>
			</view>
		</uni-popup>
		<view class="common-handle">
			<button class="common-btn" @tap="withdraw" style="background-color: #DCB736;color: white;">批量撤销</button>
			<button class="common-btn" style="background-color: #DCB736;color: white;">批量启用</button>
		</view>
	</view>
</template>

<script>
	import uniIcon from "@dcloudio/uni-ui/lib/uni-icon/uni-icon.vue"
	import uniList from '@dcloudio/uni-ui/lib/uni-list/uni-list.vue'
	import uniListItem from '@dcloudio/uni-ui/lib/uni-list-item/uni-list-item.vue'
	import uniPopup from "@dcloudio/uni-ui/lib/uni-popup/uni-popup.vue"
	import tTable from 't-table/t-table.vue';
	import tTh from 't-table/t-th.vue';
	import tTr from 't-table/t-tr.vue';
	import tTd from 't-table/t-td.vue';
	import uniPagination from "@dcloudio/uni-ui/lib/uni-pagination/uni-pagination.vue"

	export default {
		data() {
			return {
				userNiuRen: false,
				data: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
				niuren: [{
					name: '王小二',
					paiming: '1',
					shouyilv: '98.5%',
					huiche: '5%',
					shenglv: '65.5%'
				}, {
					name: '王小二',
					paiming: '1',
					shouyilv: '98.5%',
					huiche: '5%',
					shenglv: '65.5%'
				}, {
					name: '王小二',
					paiming: '1',
					shouyilv: '98.5%',
					huiche: '5%',
					shenglv: '65.5%'
				}, {
					name: '王小二',
					paiming: '1',
					shouyilv: '98.5%',
					huiche: '5%',
					shenglv: '65.5%'
				}, {
					name: '王小二',
					paiming: '1',
					shouyilv: '98.5%',
					huiche: '5%',
					shenglv: '65.5%'
				}],
				subAccountData: [{
					subAccIdn: "01s3s2r", //主键，
					tradeAccNo: "123123", //券商真实账号，
					tradeSubAccNo: "1313131", //子账号，
					tradeSubAccName: "测试策略", //子账户名称
					remark: "备注", //
					buyStrategy: "买入策略。。。", //买入策略
					sell_strategy: "卖出策略。。。。", //卖出策略
					openDate: "2018-8-8", //开户日期
					strategyPlan: "策略方案", //策略方案
					status: "0" //0未启用，A已启用，D暂停使用，C关闭，不再启用
				}, {
					subAccIdn: "01s3s2r", //主键，
					tradeAccNo: "123123", //券商真实账号，
					tradeSubAccNo: "1313131", //子账号，
					tradeSubAccName: "测试策略", //子账户名称
					remark: "备注", //
					buyStrategy: "买入策略。。。", //买入策略
					sell_strategy: "卖出策略。。。。", //卖出策略
					openDate: "2019-9-9", //开户日期
					strategyPlan: "策略方案", //策略方案
					status: "0" //0未启用，A已启用，D暂停使用，C关闭，不再启用
				}, {
					subAccIdn: "01s3s2r", //主键，
					tradeAccNo: "123123", //券商真实账号，
					tradeSubAccNo: "1313131", //子账号，
					tradeSubAccName: "测试策略", //子账户名称
					remark: "备注", //
					buyStrategy: "买入策略。。。", //买入策略
					sell_strategy: "卖出策略。。。。", //卖出策略
					openDate: "开户日期", //开户日期
					strategyPlan: "策略方案", //策略方案
					status: "0" //0未启用，A已启用，D暂停使用，C关闭，不再启用
				}, {
					subAccIdn: "01s3s2r", //主键，
					tradeAccNo: "123123", //券商真实账号，
					tradeSubAccNo: "1313131", //子账号，
					tradeSubAccName: "测试策略", //子账户名称
					remark: "备注", //
					buyStrategy: "买入策略。。。", //买入策略
					sell_strategy: "卖出策略。。。。", //卖出策略
					openDate: "开户日期", //开户日期
					strategyPlan: "策略方案", //策略方案
					status: "0" //0未启用，A已启用，D暂停使用，C关闭，不再启用
				}],
			}
		},
		components: {
			uniIcon,
			uniList,
			uniListItem,
			uniPopup,
			tTable,
			tTh,
			tTr,
			tTd,
			uniPagination
		},
		onLoad() {
			this.userNiuRen = false
		},
		methods: {
			withdraw: function() {
				console.log("withdraw")
			},
			choose1: function() {
				console.log(1)
			},
			choose2: () => {
				console.log("choose2")
			},
			choose3: () => {
				console.log("choose3")
			},
			handleTrade: (res) => {
				console.log(res)
				var tab = res.currentTarget.dataset.tab
				uni.navigateTo({
					url: "handleTrade/handleTrade?tab=" + tab
				})
			},
			tapswitch: function() {
				uni.navigateTo({
					url: '../accounts/accounts',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			},
			chooseStg: function(index) {
				console.log("chooseStg", index)
			}
		}
	}
</script>

<style>
	.header {
		width: 100%;
		display: flex;
		align-items: center;
		color: white;
		background-color: grey;
		justify-content: space-between;
		height: 100upx;
	}

	.avatar {
		width: 50upx;
		height: 50upx;
		display: block;
	}

	.title {
		width: 300upx;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}

	.head-arrow {
		width: 380upx;
		display: flex;
		align-items: center;
		justify-content: flex-end;
	}

	.profit {
		color: red;
	}

	.header-item {
		display: flex;
		align-items: center;
		margin: 10px;
	}

	.handleItem text {
		font-size: 18upx;
		color: #222222;
	}

	.logo {
		width: 60upx;
		height: 60upx;
	}

	.assetArea {
		width: 100%;
		height: 400upx;
		margin: 20upx 0;
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		justify-content: center;
	}

	.assetItem {
		background: grey;
		width: 350upx;
		height: 200upx;
		display: flex;
		flex-direction: column;
		text-align: center;
		align-items: center;
		justify-content: center;
		content: 100upx;
		border: 1px #dcb736 dashed;
	}

	.assetItem text {
		margin: 10upx;
	}

	.assetItem text:first-child {
		font-weight: 200;
		font-size: 15upx;
	}

	.handleArea {
		width: 100%;
		height: 180upx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		background: grey;
	}

	.handleItem {
		width: 100%;
		height: 100%;
		border: 1px #dcb736 dashed;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.handle-icon {
		width: 80upx;
		height: 80upx;
		margin: 15upx;
	}

	uni-list-item {
		background: grey;
		color: #DCB736
	}

	.otherList {
		width: 100%;
		position: fixed;
		bottom: 0;
	}

	.container {
		width: 100%;
		padding: 0;
		margin: 0;
		display: flex;

	}

	.accountArea {
		display: flex;
		flex-direction: column;
		align-items: center;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: space-between;
		box-sizing: border-box;
		padding: 4upx;
	}

	.subAccountArea {
		width: 100%;
		height: 240upx;
		background: grey;
		margin: 4upx 0upx;
		padding: 4upx;
	}

	.common-handle {
		display: flex;
		flex-direction: row;
		width: 100%;
		bottom: 50px;
		position: fixed;
	}

	.common-btn {
		width: 100%;
		background-color: #DCB736;
	}

	.s-head {
		display: flex;
		align-items: center;
		font-size: 24upx;
	}

	.account-handle {
		width: 100%;
		height: 100upx;
		display: flex;
		align-items: center;
	}

	.account-handle button {
		font-size: 28upx;
		width: 180upx;
		text-align: center;
		line-height: 60upx;
		height: 60upx;
	}

	.b-area {
		width: 100%;
		height: 100upx;
	}
</style>
