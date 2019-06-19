<template>
	<view class="app">
		<view class="header">
			<view @tap="chooseTab(index)" v-for="(item,index) in headList" :class="{navActive:curTab==index,navItem:curTab!=index}">{{item}}</view>
		</view>

		<view class="page" v-if="curTab==0">
			<form @submit="buyStock">
				<view class="section section_gap">
					<view class="section__title">switch</view>
					<switch name="switch" color="#DCB736" />
				</view>
				<view class="section">
					<view class="section__title">股票代码</view>
					<input name="input" placeholder="股票代码" />
				</view>
				<view class="section">
					<view class="section__title">股票价格</view>
					<input name="input" placeholder="股票价格" />
				</view>
				<view class="section">
					<view class="section__title">股票数量</view>
					<input name="input" placeholder="股票数量" />
				</view>
				<view class="section section_gap">
					<view class="section__title">仓位</view>
					<slider name="slider" activeColor="#DCB736" show-value></slider>
				</view>
				<view class="btn-area">
					<button class="submit" formType="submit">立即买入</button>
					<button class="reset" formType="reset">清空</button>
				</view>
			</form>
		</view>
		<view class="page" v-if="curTab==1">
			<form @submit="sellStock">
				<view class="section section_gap">
					<view class="section__title">switch</view>
					<switch name="switch" color="#DCB736" />
				</view>
				<view class="section">
					<view class="section__title">股票代码</view>
					<input name="input" placeholder="股票代码" />
				</view>
				<view class="section">
					<view class="section__title">股票价格</view>
					<input name="input" placeholder="股票价格" />
				</view>
				<view class="section">
					<view class="section__title">股票数量</view>
					<input name="input" placeholder="股票数量" />
				</view>
				<view class="section section_gap">
					<view class="section__title">仓位</view>
					<slider name="slider" activeColor="#DCB736" show-value></slider>
				</view>
				<view class="btn-area">
					<button class="submit" formType="submit">立即卖出</button>
					<button class="reset" formType="reset">清空</button>
				</view>
			</form>
		</view>
		<view class="page" v-if="curTab==2">
			<view class="header">
				<view class="comm-item" v-for="(item,index) in commHead">
					{{item}}
				</view>
			</view>
			<view class="tbody">
				<view class="table-row" v-for="(item,index) in commData" @click="handleComm(index)">
					<view class="table-data">{{item.stockCode}}</view>
					<view class="table-data">{{item.orderStatus}}</view>
					<view class="table-data">{{item.orderPrice}}</view>
					<view class="table-data">{{item.orderVolume}}</view>
					<view class="table-data">{{item.orderAmt}}</view>
				</view>
			</view>


			<uni-popup :show="popShow" position="middle" mode="fixed" buttonMode="right" @hidePopup="hidePopup">
				<view class="uni-center center-box">
					<view class="comm-detail">
						<view class="detail-item">股票代码：{{commDetail.stockCode}}</view>
						<view class="detail-item">委托价：{{commDetail.orderPrice}}</view>
						<view class="detail-item">委托量：{{commDetail.orderVolume}}</view>
						<view class="detail-item">委托金额：{{commDetail.orderAmt}}</view>
						<view class="detail-item">成交数量：{{commDetail.tradeVolume}}</view>
						<view class="detail-item">成交价格：{{commDetail.tradePrice}}</view>
						<view class="detail-item">成交金额：{{commDetail.tradeAmt}}</view>
					</view>
					<button type="warn" @click="cancelOrder">撤销委托</button>
				</view>
			</uni-popup>
		</view>
		<view class="page" v-if="curTab==3">
			<view class="header">
				<view class="comm-item" v-for="(item,index) in holdHead">
					{{item}}
				</view>
			</view>
			<view class="tbody">
				<view class="table-row" v-for="(item,index) in holdData" @click="handleHold(index)">
					<view class="table-data">{{item.stockCode}}</view>
					<view class="table-data">{{item.volume}}</view>
					<view class="table-data">{{item.availVolume}}</view>
					<view class="table-data">{{item.buyPrice}}</view>
					<view class="table-data">{{item.dayMarketValue}}</view>
				</view>
			</view>
			<uni-popup :show="popShow" position="middle" mode="fixed" buttonMode="right" @hidePopup="hidePopup">
				<view class="uni-center center-box">
					<view class="comm-detail">
						<view class="detail-item">股票代码：{{holdDetail.stockCode}}</view>
						<view class="detail-item">持仓数量：{{holdDetail.volume}}</view>
						<view class="detail-item">可卖数量：{{holdDetail.availVolume}}</view>
						<view class="detail-item">买入价：{{holdDetail.buyPrice}}</view>
						<view class="detail-item">收盘市值：{{holdDetail.dayMarketValue}}</view>
						<view class="detail-item">浮动盈亏：{{holdDetail.bookProfitLoss}}</view>
						<view class="detail-item">实现盈亏：{{holdDetail.profitLoss}}</view>
						<view class="detail-item">持仓起始日：{{holdDetail.openDate}}</view>
						<view class="detail-item">持仓截止日期：{{holdDetail.closeDate}}</view>
					</view>
					<button type="primary">我要卖</button>
				</view>
			</uni-popup>

			<uni-popup msg="111aa" :show="true" type="bottom"></uni-popup>

		</view>
	</view>
</template>

<script>
	import uniPopup from "@dcloudio/uni-ui/lib/uni-popup/uni-popup.vue"

	export default {

		data() {
			return {
				leftSide: "",
				rightSide: "",
				popShow: false,
				curTab: 0,
				headList: ["买入", "卖出", "撤单", "持仓"],
				commHead: ["股票代码", "处理状态", "委托价", "委托量", "委托金额"], // , "成交数量", "成交价格", "成交金额"
				commData: [{
						stockCode: "000001",
						orderIdn: "1000000",
						orderCategory: "0",
						orderVolume: 100,
						orderPrice: 6.66,
						orderAmt: 6.66,
						tradeVolume: 100,
						tradePrice: 6.66,
						tradeAmt: 666,
						orderStatus: 0
					},
					{
						stockCode: "000002",
						orderIdn: "1000000",
						orderCategory: "0",
						orderVolume: 100,
						orderPrice: 6.66,
						orderAmt: 6.66,
						tradeVolume: 100,
						tradePrice: 6.66,
						tradeAmt: 666,
						orderStatus: 0
					},
					{
						stockCode: "000003",
						orderIdn: "1000000",
						orderCategory: "0",
						orderVolume: 100,
						orderPrice: 6.66,
						orderAmt: 6.66,
						tradeVolume: 100,
						tradePrice: 6.66,
						tradeAmt: 666,
						orderStatus: 0
					}
				],
				commDetail: {
					stockCode: "000000",
					orderIdn: "1000000",
					orderCategory: "0",
					orderVolume: 100,
					orderPrice: 6.66,
					orderAmt: 6.66,
					tradeVolume: 100,
					tradePrice: 6.66,
					tradeAmt: 666,
					orderStatus: 0
				},
				holdHead: ["股票代码","持仓数量","可卖数量","买入价","收盘市值"],
				holdData:[{
					stockCode:"000000",
					volume:1000,
					availVolume:1000,
					buyPrice:6.66,
					dayMarketValue:7.77,
					bookProfitLoss:1000.23,
					profitLoss:66.66,
					openDate:2018-10-1,
					closeDate:2019-6-6
				},{
					stockCode:"000001",
					volume:1000,
					availVolume:1000,
					buyPrice:6.66,
					dayMarketValue:7.77,
					bookProfitLoss:1000.23,
					profitLoss:66.66,
					openDate:2018-10-1,
					closeDate:2019-6-6
				},{
					stockCode:"000002",
					volume:1000,
					availVolume:1000,
					buyPrice:6.66,
					dayMarketValue:7.77,
					bookProfitLoss:1000.23,
					profitLoss:66.66,
					openDate:2018-10-1,
					closeDate:2019-6-6
				}],
				holdDetail:{},
			}
		},

		components: {
			"uni-popup": uniPopup
		},
		onLoad(res) {
			this.curTab = res.tab
		},
		methods: {
			chooseTab: function(res) {
				this.curTab = res
			},
			buyStock: function(e) {
				console.log(e)
			},
			sellStock: function(e) {
				console.log("sell")
			},
			hidePopup: function(e) {
				this.popShow = false
			},
			handleComm: function(index) {
				this.commDetail = this.commData[index]
				this.popShow = true
			},
			cancelOrder: function() {
				var that = this
				uni.showModal({
					title: "确认取消？",
					confirmColor: "#DCB736",
					success(e) {
						console.log(e)
						if (e.confirm) {
							that.popShow = false
						}
					}
				})
			},
			handleHold:function(index){
				this.holdDetail = this.holdData[index]
				this.popShow = true
			}

		}
	}
</script>

<style>
	.header {
		width: 100%;
		height: 80upx;
		background-color: #eee;
		border-bottom: 1px solid #fff;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.navItem {
		width: 100%;
		padding: 18upx;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.navActive {
		width: 100%;
		padding: 18upx;
		display: flex;
		align-items: center;
		justify-content: center;
		border-bottom: 2px solid #DCB736;
		color: #DCB736;
	}

	.page {
		width: 100%;
		background: grey;
		padding: 20upx;
		box-sizing: border-box;
	}

	input {
		border: 6upx solid #DCB736;
		margin: 10upx;
	}

	button {
		margin: 10upx;
	}

	.submit {
		background: #DCB736;
	}

	.comm-table {
		border: solid 1px black;
	}

	.thead {
		display: flex;
	}

	.comm-item {
		border-bottom: 1px solid black;
		width: 300upx;
		font-size: 22upx;
		text-align: center;
	}

	.table-row {
		/* width: 300upx;
		font-size: 22upx;
		text-align: center; */
		display: flex;
	}

	.table-data {
		border-bottom: 1px solid black;
		width: 300upx;
		font-size: 28upx;
		margin: 4upx;
		padding: 8upx;
		text-align: center;
	}

	.comm-detail {
		display: flex;
		flex-direction: column;
		width: 400upx;
	}

</style>
