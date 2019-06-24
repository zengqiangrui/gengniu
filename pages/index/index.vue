<template>
	<view class="content">

		<view class="swiper">
			<swiper indicator-dots="true" autoplay="true" circular="true">
				<swiper-item>
					<view class="swiper-item uni-bg-red">A</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item uni-bg-red">B</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item uni-bg-red">C</view>
				</swiper-item>
				<image></image>
			</swiper>
		</view>

		<view class="middle">

		</view>

		<view class="fengexian">
			<view class="hengxianfar">
				<view class="hengxian"></view>
			</view>
			<view class="text">
				<text>平台综合业绩指数数据实时展示</text>
			</view>
			<view class="hengxianfar">
				<view class="hengxian"></view>
			</view>
		</view>

		<view class="zhexian">

		</view>
		<view class="bottom">
			<view class="left">
				<view class="leftone">
					<view class="textone">
						<text>跟随者，盈亏数据</text>
					</view>
					<view id="main">
					</view>
				</view>

				<view class="lefttwo">
					<view class="texttwo">
						<text>普通投资人假如本平台后盈亏情况设计图</text>
					</view>
					<view class="textthree">
						<text>盈利客户占比98.21%亏损客户占比1.79%</text>
					</view>
				</view>
			</view>
			<view class="right">
				<view class="tiaoxing" id="main2"></view>
			</view>
		</view>

	</view>
</template>

<script>
	import echarts from 'echarts'
	export default {
		name: 'hello',
		data() {
			return {
				msg: 'Welcome to Your Vue.js App'
			}
		},
		mounted() {
			echarts.init(document.getElementById('main')).setOption({
					series: {
						name: '访问来源',
						type: 'pie',
						radius: '55%',
						center: ['31%', '50%'],
						data: [{
								value: 10,
								name: '直接访问',
								itemStyle: {
									color: 'blue',
									emphasis: {
										shadowBlur: 10,
										shadowOffsetX: 0,
										shadowColor: 'rgba(0, 0, 0, 0.5)',

									}
								}
							},
							{
								value: 90,
								name: '邮件营销',
								itemStyle: {
									color: 'rgb(246,223,87)',
									emphasis: {
										shadowBlur: 10,
										shadowOffsetX: 0,
										shadowColor: 'rgba(0, 0, 0, 0.5)',

									}
								}
							},

						],
					}
				}),
				echarts.init(document.getElementById('main2')).setOption({
					grid: {
						left: '3%',
						right: '4%',
						bottom: '3%',
						containLabel: true
					},
					xAxis: [{
						type: 'category',
						axisTick: {
							show: false
						},
						data: [{
							value: '周一',
							textStyle: {
								fontSize: "8"
							}
						}, {
							value: '周二',
							textStyle: {
								fontSize: "8"
							}
						}, {
							value: '周三',
							textStyle: {
								fontSize: "8"
							}
						}, {
							value: '周四',
							textStyle: {
								fontSize: "8"
							}
						}, {
							value: '周五',
							textStyle: {
								fontSize: "8"
							}
						}, ],
					}],
					yAxis: [{
							type: 'value',	
						}]
						,
					series: [{
							name: '利润',
							type: 'bar',
							label: {
								normal: {
									show: false,
									position: 'inside'
								}
							},
							// data: [200, 170, 240, 244, 200, ]
							data: [{
								value: '200',
								textStyle: {
									fontSize: "8"
								}
							}, {
								value: '170',
								textStyle: {
									fontSize: "8"
								}
							}, {
								value: '240',
								textStyle: {
									fontSize: "8"
								}
							}, {
								value: '244',
								textStyle: {
									fontSize: "8"
								}
							}, {
								value: '200',
								textStyle: {
									fontSize: "8"
								}
							}, ]
						},

						{
							name: '支出',
							type: 'bar',
							stack: '总量',
							label: {
								normal: {
									show: false,
									position: 'left'
								}
							},
							// data: [-120, -132, -101, -134, -190, ]
							data: [{
								value: '-120',
								textStyle: {
									fontSize: "8"
								}
							}, {
								value: '-132',
								textStyle: {
									fontSize: "8"
								}
							}, {
								value: '-101',
								textStyle: {
									fontSize: "8"
								}
							}, {
								value: '-134',
								textStyle: {
									fontSize: "8"
								}
							}, {
								value: '-190',
								textStyle: {
									fontSize: "8"
								}
							}, ]
						}
					]
				})
		}
	}
</script>

<style>
	#main2 {
		height: 300upx;
		width: 300upx;
	}

	.leftone {
		width: 200upx;
		height: 100%;
	}

	.lefttwo {
		width: 200upx;
		height: 100%;
	}

	.textone {
		margin-top: 22upx;
		width: 180upx;
		height: 20upx;
		color: gold;
		font-size: 14upx;
	}

	.textthree {
		width: 190upx;
		height: 50upx;
		font-size: 14upx;
		margin-top: 20upx;
		color: rgb(151, 151, 151);
		text-align: left;
		margin-left: 75upx;
	}

	.texttwo {
		width: 190upx;
		height: 50upx;
		font-size: 14upx;
		margin-top: 130upx;
		margin-left: 75upx;
		color: rgb(151, 151, 151);
		word-break: break-word;
		text-align: left;
	}

	.bottom {
		height: 350upx;
		width: 100%;
		background-color: #C6E746;
		display: flex;
		flex-flow: row;
	}

	.left {
		height: 350upx;
		width: 450upx;
		background-color: rgb(80, 80, 80);
		display: flex;
		flex-flow: row;
	}

	#main {
		height: 300upx;
		width: 600upx;
		background-color: rgb(80, 80, 80)
	}

	.right {
		height: 320upx;
		width: 40%;
		background-color: #3CC51F;
		margin-top: 30upx;
	}

	.zhexian {
		height: 300upx;
		width: 100%;
		background-color: #D2E0E6;
	}

	.fengexian {
		height: 40upx;
		width: 100%;
		background-color: pink;
		display: flex;
		flex-flow: row;
		align-items: center;
		justify-content: center;
	}

	.hengxianfar {
		height: 40upx;
		width: 160upx;
		background-color: #2B81AF;
	}

	.hengxian {
		height: 20upx;
		width: 160upx;
		background: #3CC51F;
		border-bottom: 1upx solid red;
	}

	.text {
		width: 420upx;
		height: 40upx;
		font-size: 30upx;
		color: rgb(168, 138, 69);
	}

	.middle {
		height: 190upx;
		width: 100%;
		background-color: #007AFF;
	}

	.swiper {
		height: 300upx;
		width: 100%;
		background-color: rgb(97, 97, 97);
	}

	.swiper-item {
		height: 300upx;
		width: 100%;
	}

	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
