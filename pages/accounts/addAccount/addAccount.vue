<template>
	<view class="content">
		<view style="height: 1px;margin-top: 50px;"></view>
		<view class="row">
			<view class="row-l">主账户号</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入主账户号" />
			</view>
		</view>
		<view style="height: 1px;margin-top: 10px;"></view>
		<view class="row">
			<view class="row-l">子账户号</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入子账户号" />
			</view>
		</view>
		<view style="height: 1px;margin-top: 10px;"></view>
		<view class="row">
			<view class="row-l">主账户昵称</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入主账户昵称" />
			</view>
		</view>
		<view style="height: 1px;margin-top: 10px;"></view>
		<view class="row">
			<view class="row-l">备注</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入备注信息..." />
			</view>
		</view>
		<view style="height: 1px;margin-top: 10px;"></view>
		<view>
			<button class="add" @tap="add">立即添加</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			add:function(){
				uni.navigateBack()({
					url: '../accounts',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
				// uni.navigateBack({
				// 	
				// });
			}
		}
	}
</script>

<style>
	.content {
		width: 90%;
		height: 100%;
		margin-left: 5%;
	}
	.row {
		display: flex;
		flex-direction: row;
		width: 100%;
		height: 40px;
		/* background-color: #FFFFFF; */
		border-bottom: 1px solid #FFD700;
	
	}
	
	.row-l {
		width: 30%;
		height: 40px;
		color: #DCB736;
		font-size: 18px;
		display: flex;
		align-items: center;
	}
	
	.row-r {
		width: 70%;
		height: 40px;
		color: #dcb736;
		font-size: 18px;
		display: flex;
		align-items: center;
	}
	.add {
		color: #FFFFFF;
		background-color: #6641E2;
		font-size: 15px;
		width: 100%;
		height: 35px;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	
</style>
