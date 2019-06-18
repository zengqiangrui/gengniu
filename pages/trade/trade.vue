<template>
	<view class="content">
		<uni-list >
			<uni-list-item @tap="tapswitch" title="长城证券" note="点击切换主账户"  thumb="/static/icons/greatwall.jpg" ></uni-list-item>
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
			<view class="handleItem" data-tab = 0 @tap="handleTrade">
				<image class="handle-icon" src="/static/icons/buy.png" mode="scaleToFill"></image>
				<text>买入</text>
			</view>
			<view class="handleItem" data-tab = 1 @tap="handleTrade">
				<image class="handle-icon" src="/static/icons/sell.png"></image>
				<text>卖出</text>
			</view>
			<view class="handleItem" data-tab = 2 @tap="handleTrade">
				<image class="handle-icon" src="/static/icons/che2.png"></image>
				<text>撤单</text>
			</view>
			<view class="handleItem" data-tab = 3 @tap="handleTrade">
				<image class="handle-icon" src="/static/icons/hold.png"></image>
				<text>持仓</text>
			</view>
		</view>
		<view class="otherList">
			<uni-list>
				<uni-list-item @click="choose1" title="切换子账户"></uni-list-item>
				<uni-list-item @click="choose2" title="交易规则"></uni-list-item>
				<uni-list-item @tap="choose3" title="意见反馈"></uni-list-item>
			</uni-list>
		</view>
	</view>
<!-- 	
	<view v-else>
		
		我只是普通人

	</view> -->
</template>

<script>
	import uniIcon from "@dcloudio/uni-ui/lib/uni-icon/uni-icon.vue"
	import uniList from '@dcloudio/uni-ui/lib/uni-list/uni-list.vue'
	import uniListItem from '@dcloudio/uni-ui/lib/uni-list-item/uni-list-item.vue'
	export default {
		data() {
			return {
				
			}
		},
		components: {
			uniIcon,
			uniList,
			uniListItem
		},
		onLoad() {
			this.userNiuRen = true
		},
		methods: {
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
					url: "handleTrade/handleTrade?tab="+tab
				})
			},
			tapswitch:function(){
				uni.navigateTo({
					url: '../accounts/accounts',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
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
</style>
