<template>
	<view class="content">
		<view class="header">
			<view class="logo">
				<image src="../../static/icons/greatwall.jpg" mode=""></image>
			</view>
			<view class="head-msg">切换子账户</view>
			<uni-icon type="contact" color="white"></uni-icon>
		</view>
<!-- 		<view class="assetArea">
			<view class="assetItem">
				<text>总资产</text>
				<text>10000.00</text>
			</view>
			<view class="assetItem">
				<text>浮动盈亏</text>
				<text>10000.00</text>
			</view>
			<view class="assetItem">
				<text>总市值</text>
				<text>10000.00</text>
			</view>
			<view class="assetItem">
				<text>总资产</text>
				<text>10000.00</text>
			</view>
		</view> -->
	</view>


</template>

<script>
	import uniIcon from "@dcloudio/uni-ui/lib/uni-icon/uni-icon.vue"

	export default {
		data() {
			return {

			}
		},
		components: {
			uniIcon
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		height: 100upx;
		background: darkgrey;
		color: white;
		display: flex;
		align-items: center;
		justify-content: flex-end;
		font-size: 12upx;
	}

	.assetArea {
		width: 100%;
		height: 200upx;
	}
</style>
