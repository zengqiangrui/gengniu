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
			<!-- <view class="header">
				<view class="comm-item" v-for="(item,index) in commItem">
					{{item}}
				</view>
			</view>
			<view class="tbody">
				
			</view> -->
			<table border="1" class="comm-table">
				<thead class="thead">
					<th  class="comm-item" v-for="(item,index) in commItem">{{item}}</th>
				</thead>
				<tr>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
				</tr>
				<tr>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
					<td>1</td>
				</tr>
			</table>
			
		</view>
		<view class="page" v-if="curTab==3">
			4
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				curTab: 0,
				headList: ["买入", "卖出", "撤单", "持仓"],
				commItem:["股票代码","处理状态","委托价","委托量","委托金额","成交数量","成交价格","成交金额"]
			}
		},
		onLoad(res) {

			this.curTab = res.tab
			console.log(2 ** 3)
		},
		methods: {
			chooseTab: function(res) {
				this.curTab = res
			},
			buyStock: function(e) {
				console.log(e)
			},
			sellStock:function(e){
				console.log("sell")
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
	
	.comm-table{
		border: solid 1px black;
	}
	
	.thead{
		display: flex;
	}
	
	.comm-item{
		border: 1px solid black;
	}
</style>
