<template>
	<view class="content">


		<view style="height: 1px;margin-top: 50px;"></view>
		<view class="row">
			<view class="row-l">
				<uni-icon type="phone" color="#2AC845" size=20></uni-icon>
			</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入手机号码" />
			</view>
		</view>



		<view style="height: 1px;margin-top: 15px;"></view>
		<view class="row">
			<view class="row-l">
				<uni-icon type="locked" color="#2AC845" size=20></uni-icon>
			</view>
			<view class="row-r">
				<input type="password" style="font-size: 15px;" placeholder="请输入密码" />
			</view>
		</view>


		<view style="height: 1px;margin-top: 20px;"></view>
		<view>
			<button class="login" @tap="login">login</button>
		</view>

		<view style="height: 1px;margin-top: 15px;"></view>
		<view class="pas">
			<view class="pas-l" @tap="regi">立即注册</view>
			<view class="pas-r" @tap="pwd">忘记密码</view>
		</view>

		<!-- <uni-icon type="locked" color="#2AC845" size=35></uni-icon> -->

		<view class="bottom">
			<view class="bottom-u">
				<view class="bottom-u-m">———————— 第三方登录 ————————</view>
			</view>
			<view class="bottom-d">
				<view class="bottom-d-l">
					<uni-icon type="qq" color="#2AC845" size=30></uni-icon>
				</view>
				<view class="bottom-d-r">
					<uni-icon type="weixin" color="#4169E1" size=35></uni-icon>
				</view>
			</view>
		</view>


	</view>

</template>

<script>
	import uniIcon from "@dcloudio/uni-ui/lib/uni-icon/uni-icon.vue"
	export default {
		data() {
			return {

			}
		},
		methods: {
			regi:function(){
				uni.navigateTo({
					url: '../register/register',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			},
			pwd:function(){
				uni.navigateTo({
					url: '../pwd/pwd',
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			},
			login:function(){
				uni.switchTab({
					url: '../../trade/trade',
				})
			}
		},
		components: {
			uniIcon
		}
	}
</script>

<style>
	.content {
		width: 90%;
		height: 100%;
		margin-left: 5%;
	}

	.font {
		color: white;
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
		width: 15%;
		height: 40px;
		color: #DCB736;
		font-size: 18px;
		display: flex;
		align-items: center;
	}

	.row-r {
		width: 85%;
		height: 40px;
		color: #dcb736;
		font-size: 18px;
		display: flex;
		align-items: center;
	}

	.login {
		color: #FFFFFF;
		background-color: #6641E2;
		font-size: 15px;
		width: 100%;
		height: 35px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.pas {
		width: 100%;
		height: 20px;
		display: flex;
		flex-direction: row;
	}

	.pas-l {
		width: 50%;
		height: 100%;
		font-size: 13px;
		color: #DCB736;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.pas-r {
		width: 50%;
		height: 100%;
		font-size: 13px;
		color: red;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.bottom {
		width: 90%;
		height: 100px;
		/* background-color: #6641E2; */
		position: fixed;
		bottom: 0;
	}

	.bottom-u {
		height: 10px;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
	}

	.bottom-d {
		height: 90px;
		width: 100%;
		display: flex;
	}

	.bottom-u-m {
		font-size: 12px;
		color: #DCB736;
	}

	.bottom-d-l {
		width: 50%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.bottom-d-r {
		width: 50%;
		height: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>
