<template>
	<view>
		<button class="choose" @tap="showPopup"> 选择牛人</button>
		<view>dfghjklxdcfghvjkl;zsdxcfgvhbjnkml;dfcgvhbjkl;xnkml,;</view>
	
		<!-- 弹出层 -->
		<view class="popup" v-if="isShow">
			<view class="title">选择牛人</view>
			<view class="tishi">*您最少要选择5-10个牛人</view>
			<!-- 表格 -->
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
									<checkbox style="transform:scale(0.5)" ></checkbox>
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
			<button class="close" @tap="closePopup">关闭</button>
		</view>

		<!-- 做黑色阴影颜色 -->
		<view class="uni-mask" v-if="isShow">
		</view>

	</view>
</template>

<script>
	import tTable from 't-table/t-table.vue';
	import tTh from 't-table/t-th.vue';
	import tTr from 't-table/t-tr.vue';
	import tTd from 't-table/t-td.vue';
	import uniPagination from "@dcloudio/uni-ui/lib/uni-pagination/uni-pagination.vue"

	export default {

		components: {
			tTable,
			tTh,
			tTr,
			tTd,
			uniPagination
		},
		data() {
			return {
				isShow: false,
				niuren:
					// {
					// 		name: '王小二',
					// 		paiming:'1',
					// 		shouyilv:'98.5%',
					// 		huiche:'5%',
					// 		shenglv:'65.5%'				
					// }
					[{
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
					},]
			};
		},
		methods: {
			showPopup: function() {
				this.isShow = true
			},
			closePopup: function() {
				this.isShow = false
			}
		}
	}
</script>

<style>
	t-tr:nth-child(2n+1){
		background: rgb(181,181,181);
	}
	t-tr:first-child{
		background: rgb(156,156,156);
	}	


	.box {
		width: 100%;
		height: 620upx;
		font-size: 12px;
		position: absolute;
	}

	.warp {
		position: absolute;
		width: 100%;
		height: 100%;
	}


	.fanye {
		height: 50upx;
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		position: absolute;
		bottom: 80upx;
		
	}

	.close {
		height: 30px;
		width: 108px;
		position: absolute;
		bottom: 0px;
		margin-left: 31%;
		line-height: 30px;

	}

	.title {
		height: 32px;
		width: 100px;
		line-height: 32px;
		text-align: center;
		color: white;
		margin-left: 30%;
	}

	.ima {
		height: 100px;
		width: 100%;
	}

	.tishi {
		height: 15px;
		width: 200px;
		color: white;
		line-height: 15px;
		text-align: center;
		margin-left: 10%;
		font-size: 10px;
	}

	.choose {
		background-color: #3CC51F;
	}

	.popup {
		background-color: RGB(156, 156, 156);
		height: 65%;
		width: 77%;
		z-index: 2;
		position: absolute;
		top: 20%;
		left: 12%;
	}

	.uni-mask {
		height: 100%;
		width: 100%;
		z-index: -1;
		background: rgba(0, 0, 0, 0.3);
	}
</style>
