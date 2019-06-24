<template>
	<view class="content">

		<view class="head">
			<view class="h-avator">
				<view class="h-avator-i"></view>
			</view>
			<view class="h-m">
				<view class="h-m-u">UserName</view>
				<view class="h-m-d">UserDescription</view>
			</view>
			<view class="h-r">
				<view class="h-r-i">+跟单牛人</view>
			</view>
		</view>

		<view class="second">
			<view class="second-l">
				<view style="color: #FF0000;">
					<h2>2550%</h2>
				</view>
				<view style="color: #FFFFFF;">
					<h5> 总收益率</h5>
				</view>
			</view>
			<view class="second-r">
				<view class="second-r-u" style="color: #FFFFFF;">
					<h6>净值:73334</h6>
				</view>
				<view class="second-r-d" style="color: #FFFFFF;">
					<h6>排名:109</h6>
				</view>
			</view>
		</view>

		<view class="table">
			<view class="table-u">
				<view class="table-cell">
					<view class="table-tit">月均收入</view>
					<view class="table-data">4.55%</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">当月累计收益</view>
					<view class="table-data">+1660%</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">年累计收益</view>
					<view class="table-data">+966%</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">胜率</view>
					<view class="table-data">260%</view>
				</view>
			</view>
			<view class="table-d">
				<view class="table-cell">
					<view class="table-tit">持股周期</view>
					<view class="table-data">998(天)</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">月均交易</view>
					<view class="table-data">32(天)</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">初次交易</view>
					<view class="table-data">1997-01-08</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">最近交易</view>
					<view class="table-data">2099-12-31</view>
				</view>
			</view>
		</view>


		<view class="charts">
			<view class="charts-u">
				<swiper class="swi" @change="change" :current="current">
					<swiper-item>
						<view class="swi-1">
							<view class="swi-1-l">
								<view id="main" style="width: 100%;height:100%;"></view>
							</view>
							<view class="swi-1-r">
								<view class="det">
									<view class="det-l">
										<view class="det-l-l">
											<view class="color1"></view>
										</view>
										<view class="det-l-r">银行B端</view>
									</view>
									<view class="det-r">99.01%</view>
								</view>
								<view class="det">
									<view class="det-l">
										<view class="det-l-l">
											<view class="color2"></view>
										</view>
										<view class="det-l-r">顺和电气</view>
									</view>
									<view class="det-r">99.01%</view>
								</view>
								<view class="det">
									<view class="det-l">
										<view class="det-l-l">
											<view class="color3"></view>
										</view>
										<view class="det-l-r">高盛控股</view>
									</view>
									<view class="det-r">99.01%</view>
								</view>
								<view class="det">
									<view class="det-l">
										<view class="det-l-l">
											<view class="color4"></view>
										</view>
										<view class="det-l-r">其他股票</view>
									</view>
									<view class="det-r">99.01%</view>
								</view>
								<view class="det">
									<view class="det-l">
										<view class="det-l-l">
											<view class="color5"></view>
										</view>
										<view class="det-l-r">可用资金</view>
									</view>
									<view class="det-r">99.01%</view>
								</view>

							</view>
						</view>
					</swiper-item>
					<swiper-item>
						<view class="swi-r">
							<view id="main2" style="width: 100%;height:200px;margin-left: 2%;"></view>
						</view>
					</swiper-item>
				</swiper>
			</view>
			<view class="charts-d">
				<view class="charts-d-i">
					<view class="charts-d-i-l" @tap="tapToLeft">收益曲线</view>
					<view class="charts-d-i-r" @tap="tapToRight">仓位配置</view>
				</view>
			</view>
		</view>

		<view style="width: 100%;height: 3px;background-color: #8F8F94;margin-top: 5px;margin-bottom: 5px;"></view>
		<view class="footer">
			<view class="footer-u">当前持仓(66)</view>
			<view class="footer-d">
				<view class="table-cell">
					<view class="table-tit">股票名称</view>
					<view class="table-data">厦门信达</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">现价/成本</view>
					<view class="table-data">1099</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">持仓/仓位</view>
					<view class="table-data">900</view>
				</view>
				<view class="table-cell">
					<view class="table-tit">收益/盈亏</view>
					<view class="table-data">110%</view>
				</view>
			</view>
		</view>





	</view>
</template>

<script>
	import echarts from "echarts/dist/echarts.js"

	export default {
		data() {
			return {
				current: 0
			}
		},
		methods: {
			change: function(e) {
				console.log(e)
			},
			tapToLeft: function() {
				this.current = 0
			},
			tapToRight: function() {
				this.current = 1
			}
		},
		mounted() {
			echarts.init(document.getElementById('main2')).setOption({
				xAxis: {
					type: 'category',
					data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
				},
				yAxis: {
					type: 'value'
				},
				series: [{
					data: [3.5, 4.2, 1.6, 2.0, 7.5, 3.3, 1000],
					type: 'line'
				}],
			});
			
			
			echarts.init(document.getElementById('main')).setOption({
				series: {
					name: 'data',
					type: 'pie',
					radius: ['50%', '70%'],
					avoidLabelOverlap: false,
					label: {
						normal: {
							show: false,
							position: 'center'
						},
						emphasis: {
							show: true,
							textStyle: {
								fontSize: '30',
								fontWeight: 'bold'
							}
						}
					},
					labelLine: {
						normal: {
							show: false
						}
					},
					data: [{
							value: 735,
							// name: '直接访问'
						},
						{
							value: 310,
							// name: '邮件营销'
						},
						{
							value: 234,
							// name: '联盟广告'
						},
						{
							value: 135,
							// name: '视频广告'
						},
						{
							value: 1548,
							// name: '搜索引擎'
						}
					]
				}
			});
		}
	}
</script>

<style>
	.content {
		width: 94%;
		height: 100%;
		margin-left: 3%;
	}

	.head {
		width: 100%;
		height: 60px;
		display: flex;
		flex-direction: row;
	}

	.h-avator {
		width: 20%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.h-m {
		width: 55%;
		height: 100%;
	}

	.h-r {
		width: 25%;
		height: 100%;
		display: flex;
		align-items: center;
	}

	.h-m-u {
		width: 100%;
		height: 50%;
		display: flex;
		align-items: flex-end;
		color: #FFC0CB;
		font-size: 16px;
	}

	.h-m-d {
		width: 100%;
		height: 50%;
		display: flex;
		align-items: flex-end;
		color: #FFC0CB;
		font-size: 14px;
	}

	.h-avator-i {
		width: 45px;
		height: 45px;
		background-color: #808080;
	}

	.h-r-i {
		width: 100%;
		height: 50%;
		border: 1px solid #6641E2;
		font-size: 12px;
		display: flex;
		align-items: center;
		justify-content: center;
		color: #FFFFFF;
	}



	.second {
		width: 100%;
		height: 60px;
		display: flex;
		flex-direction: row;
	}

	.second-l {
		width: 70%;
		height: 100%;
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.second-r {
		width: 30%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}


	.table {
		width: 100%;
		height: 140px;
	}

	.table-u {
		width: 100%;
		height: 50%;
		display: flex;
		flex-direction: row;
	}

	.table-d {
		width: 100%;
		height: 50%;
		display: flex;
		flex-direction: row;
	}

	.table-cell {
		width: 25%;
		height: 100%;
	}

	.table-tit {
		width: 100%;
		height: 50%;
		/* background-color: #6641E2; */
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 13px;
		color: #DCB736;
	}

	.table-data {
		width: 100%;
		height: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 13px;
		color: #FFFFFF;
	}

	.charts {
		width: 100%;
		height: 200px;
		/* border: 1px solid #6641E2; */
	}

	.charts-u {
		width: 100%;
		height: 170px;
	}

	.charts-d {
		width: 100%;
		height: 30px;
		display: flex;
		justify-content: center;
	}

	.charts-d-i {
		width: 60%;
		height: 100%;
		display: flex;
		flex-direction: row;
	}

	.charts-d-i-l {
		width: 50%;
		height: 100%;
		border: 1px solid #DCB736;
		color: #FFFFFF;
		font-size: 12px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.charts-d-i-r {
		width: 50%;
		height: 100%;
		border: 1px solid #DCB736;
		color: #FFFFFF;
		font-size: 12px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.swi {
		width: 100%;
		height: 100%;
	}


	.footer {
		width: 100%;
		height: 90px;
	}

	.footer-u {
		width: 100%;
		height: 20px;
		color: #FFFFFF;
		font-size: 13px;
		display: flex;
		align-items: center;
	}

	.footer-d {
		width: 100%;
		height: 70px;
		display: flex;
		flex-direction: row;
	}

	.swi-1 {
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: row;
	}

	.swi-1-l {
		width: 50%;
		height: 100%;
	}

	.swi-1-r {
		width: 50%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.det {
		width: 100%;
		height: 20px;
		display: flex;
		flex-direction: row;	
	}

	.det-l {
		width: 50%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: row;
	}

	.det-r {
		width: 50%;
		height: 100%;
		font-size: 12px;
		display: flex;
		align-items: center;
		justify-content: center;
		color: #8F8F94;
	}

	.det-l-l {
		width: 20%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.det-l-r {
		width: 80%;
		height: 100%;
		color: #8F8F94;
		font-size: 12px;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.color1{
		width: 10px;
		height: 10px;
		background-color: #9fdabf;
	}
	.color2{
		width: 10px;
		height: 10px;
		background-color: #334b5c;
	}
	.color3{
		width: 10px;
		height: 10px;
		background-color: #c23531;
	}
	.color4{
		width: 10px;
		height: 10px;
		background-color: #6ab0b8;
	}
	.color5{
		width: 10px;
		height: 10px;
		background-color: #d48265;
	}
	.swi-r{
		width: 100%;
		height: 100%;
	}
</style>
