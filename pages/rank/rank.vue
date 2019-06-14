<template>
	<view class="mui-content">
		<!--<view class="topcontext">-->
		<view class="content">
			<view class="bangdan">
				<picker :range="condition">
					<view>筛选条件</view>
				</picker>
			</view>
			<view class="bangdanOne">
				<picker mode="date">
					<view>开始时间</view>
				</picker>
			</view>
			<view class="bangdanOne">
				<picker mode="date">
					<view>截止时间</view>
				</picker>
			</view>
			<view class="bangdanTwo">
				<picker :range="duration" .@change="changePicker">
					<view>周期</view>
				</picker>
			</view>
		</view>
		<!--</view>-->
		<view id="niu">
			<view class="head" v-for="site in sites">
				<view class="top">
					<view class="topSun">
						<view class="headone">
							<view class="niuren"></view>
							<view class="headtwo">
								<view class="name">{{site.name}}</view>
								<view class="jianjie">{{site.jianjie}}</view>
							</view>
						</view>
						<view class="guanzhu">
							+&nbsp;策略订阅
						</view>
					</view>
				</view>
				<view class="bottom">
					<view class="bottomLeft">
						<view class="shouyiOne">{{site.zongshouyi}}</view>
						<view class="shouyitwo">总收益率</view>
					</view>
					<view class="bottomMiddle">
						<view class="shouyiOne">{{site.yueshouyi}}</view>
						<view class="shouyitwo">月均收益率</view>
					</view>
					<view class="bottomRight">
						<view class="shouyiOne">{{site.shenglv}}</view>
						<view class="shouyitwo">胜率</view>
					</view>
				</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				duration: ["年", "季", "月", "周"],
				condition: ["主账户", "子账户", "策略方案", "策略作者"],

				sites: [{
						name: '股琴A',
						jianjie: '曾获世界影响华人大奖牛逼哔哔哔哔哔哔哔哔哔哔',
						zongshouyi: '1922.55%',
						yueshouyi: '74.%',
						shenglv: '68.5%',
					},
					{
						name: '股琴B',
						jianjie: '人大奖牛逼哔哔哔哔哔哔哔哔哔哔',
						zongshouyi: '1922.55%',
						yueshouyi: '74.17%',
						shenglv: '68%',
					},
					{
						name: '股琴A',
						jianjie: '曾获世界影响华人大奖牛逼哔哔哔哔哔哔哔哔哔哔',
						zongshouyi: '1922.55%',
						yueshouyi: '74.%',
						shenglv: '68.5%',
					},
					{
						name: '股琴B',
						jianjie: '人大奖牛逼哔哔哔哔哔哔哔哔哔哔',
						zongshouyi: '1922.55%',
						yueshouyi: '74.17%',
						shenglv: '68%',
					},
					{
						name: '股琴B',
						jianjie: '人大奖牛逼哔哔哔哔哔哔哔哔哔哔',
						zongshouyi: '1922.55%',
						yueshouyi: '74.17%',
						shenglv: '68%',
					},
					{
						name: '股琴B',
						jianjie: '人大奖牛逼哔哔哔哔哔哔哔哔哔哔',
						zongshouyi: '1922.55%',
						yueshouyi: '74.17%',
						shenglv: '68%',
					},
					{
						name: '股琴B',
						jianjie: '人大奖牛逼哔哔哔哔哔哔哔哔哔哔',
						zongshouyi: '1922.55%',
						yueshouyi: '74.17%',
						shenglv: '68%',
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			changePicker: res => {
				console.log()
			}
		}
	}
</script>

<style>
	.content {
		background-color: #222222;
		height: 28px;
		width: 100%;
		border-bottom: rgb(190, 190, 190);
		border-style: solid;
		border-width: 1px;
		display: flex;
		flex-flow: row;
		position: fixed;
		top: 0px;

	}

	.topcontext {
		height: 25px;
		width: 100%;

		position: fixed;
		top: 45px;
	}

	.bangdan {
		height: 100%;
		width: 25%;
		/*background-color: #222222;*/
		text-align: center;
		font-size: 12px;
		align-items: center;
		line-height: 28px;
		color: white;
	}

	.bangdanOne {
		height: 100%;
		width: 25%;
		/*background-color: #222222;*/
		text-align: center;
		font-size: 12px;
		align-items: center;
		line-height: 28px;
		color: white;
	}

	.bangdanTwo {
		height: 100%;
		width: 25%;
		/*background-color: b;*/
		text-align: center;
		font-size: 12px;
		align-items: center;
		line-height: 28px;
		color: white;
	}

	.head {
		height: 105px;
		width: 100%;
		background-color: #222222;
		display: flex;
		flex-flow: column;
	}

	#niu {
		margin-top: 40px;
	}

	.niuren {
		height: 40px;
		width: 40px;
		background-color: pink;
		margin-left: 10px;
		margin-top: 16px;
		border-radius: 25px;
	}

	.headone {
		display: flex;
		height: 70px;
		width: 400px;
		display: flex;
	}

	.headtwo {
		margin-top: 20px;
		margin-left: 7px;
		height: 50px;
		width: 150px;
	}

	.name {
		color: white;
		height: 23px;
		width: 100px;
		font-size: 15px;
		margin-top: -5px;
	}

	.jianjie {
		color: rgb(190, 190, 190);
		height: 17px;
		width: 150px;
		font-size: 10px;
		margin-top: 2px;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}

	.guanzhuSun {
		height: 17px;
		width: 78px;

	}

	.guanzhu {
		color: white;
		border-style: solid;
		border-width: 1px;
		border-color: white;
		height: 17px;
		width: 78px;
		margin-top: 20px;
		margin-right: 10px;
		font-size: 8px;
		line-height: 17px;
		align-items: center;
		text-align: center;
	}

	.top {
		height: 74px;
		width: 100%;
		display: flex;
		flex-flow: row;
	}

	.topSun {
		height: 74px;
		width: 100%;
		display: flex;
		flex-flow: row;

	}

	.bottom {
		height: 30px;
		width: 100%;
		/*background-color: red;*/
		display: flex;
		flex-flow: row;
	}

	.bottomLeft {
		height: 37px;
		width: 33%;
		/*	background-color: palegreen;*/
		margin-top: -10px;
		display: flex;
		flex-flow: column;
		align-items: center;
	}

	.bottomRight {
		height: 37px;
		width: 33%;
		/*background-color: paleturquoise;*/
		margin-top: -10px;
		display: flex;
		flex-flow: column;
		align-items: center;
	}

	.bottomMiddle {
		height: 37px;
		width: 34%;
		/*background-color: palegreen;*/
		margin-top: -10px;
		display: flex;
		flex-flow: column;
		align-items: center;
	}

	.shouyiOne {
		height: 17px;
		width: 70px;
		/*	background-color: papayawhip;*/
		font-size: 12px;
		color: red;
		text-align: center;
	}

	.shouyitwo {
		height: 17px;
		width: 70px;
		/*	background-color: paleturquoise;*/
		color: rgb(190, 190, 190);
		font-size: 9px;
		text-align: center;
	}
</style>
