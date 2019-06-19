<template>
	<view class="content">

		<view class="list">
			
			
			<view class="mainList" @tap="showdetail">
				<view class="mainList-l">
					<view class="mainList-l-i">
						<image src="../../static/icons/greatwall.jpg" mode="" style="width: 100%;height: 100%;"></image>
					</view>
				</view>
				<view class="mainList-r">
					<view class="mainList-r-u">长城证券</view>
					<view class="mainList-r-d">长城证券</view>
				</view>
				<view class="mainList-addBtn">
					<view class="mainList-addBtn-addBtn" @tap.stop="add">添加子帐号</view>
				</view>
			</view>
			
			
			<view class="subList" v-if="show">
				<view class="s-mainList">
					<view class="mainList-l">
						<view class="mainList-l-i"></view>
					</view>
					<view class="mainList-r">
						<view class="mainList-r-u">子帐号</view>
						<view class="mainList-r-d">子帐号</view>
					</view>
				</view>
				<view class="s-mainList">
					<view class="mainList-l">
						<view class="mainList-l-i"></view>
					</view>
					<view class="mainList-r">
						<view class="mainList-r-u">子帐号</view>
						<view class="mainList-r-d">子帐号</view>
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
				show:false
			}
		},
		methods: {
			showdetail:function(){
				if(this.show){
					this.show = false
				}else{
					this.show = true
				}
			},
			add:function(){
				uni.navigateTo({
					url: 'addAccount/addAccount',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		},
		components: {

		},
	}
</script>



<style>
	.content {
		width: 90%;
		height: 100%;
		margin-left: 5%;
	}
	.list{
		width: 100%;
		display: flex;
		flex-direction: column;
	}
	.mainList {
		width: 100%;
		height: 50px;
		display: flex;
		flex-direction: row;
		border: 1px solid #DCB736;
	}

	.mainList-l {
		width: 20%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.mainList-r {
		width: 50%;
		height: 100%;
	}
	.mainList-addBtn{
		width: 30%;
		height: 100%;
		background-color: #6641E2;
		display: flex;
		align-items: center;
		justify-content: center;
		color: #FFC0CB;
		font-size: 13px;
	}
	.mainList-l-i {
		width: 35px;
		height: 35px;
		background-color: #8F8F94;
	}

	.mainList-r-u {
		width: 100%;
		height: 50%;
		color: #DCB736;
		font-size: 15px;
		display: flex;
		align-items: flex-end;
	}

	.mainList-r-d {
		width: 100%;
		height: 50%;
		color: #DCB736;
		font-size: 15px;
		display: flex;
		align-items: flex-end;
	}

	.subList {
		width: 100%;
	}
	.s-mainList{
		margin-top: 1px;
		width: 100%;
		height: 50px;
		display: flex;
		flex-direction: row;
		border: 1px solid #6641E2;
	}
</style>
