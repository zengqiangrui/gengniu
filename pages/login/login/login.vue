<template>
	<view class="content">
		
		
		<view style="height: 1px;margin-top: 50px;"></view>
		<view class="row">
			<view class="row-l">手机号码</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入手机号码" />
			</view>
		</view>
		<view style="height: 1px;margin-top: 15px;"></view>
		<view class="row">
			<view class="row-l">密码</view>
			<view class="row-r">
				<input type="password" style="font-size: 15px;" placeholder="请输入密码" />
			</view>
		</view>
		
		
		<view style="height: 1px;margin-top: 20px;"></view>
		<view>
			<button class="login">login</button>
		</view>
		
		<view style="height: 1px;margin-top: 15px;"></view>
		<view class="pas">
			<view class="pas-l">立即注册</view>
			<view class="pas-r">忘记密码</view>
		</view>

		<view class="bottom">
			<view class="bottom-u" style="display: flex;flex-direction: row;height: 10px;">
				<view class="bottom-u-m">———————— 第三方登录 ————————</view>
			</view>
			<view class="bottom-d"></view>
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
	.row-l{
		width: 30%;
		height: 40px;
		color: #DCB736;
		font-size: 18px;
		display: flex;
		align-items: center;
	}
	.row-r{
		width: 70%;
		height: 40px;
		color: #dcb736;
		font-size: 18px;
		display: flex;
		align-items: center;
	}
	.login{
		color: #FFFFFF;
		background-color: #6641E2;
		width: 100%;
		height: 35px;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.pas{
		width: 100%;
		height: 20px;
		display: flex;
		flex-direction: row;
	}
	.pas-l{
		width: 50%;
		height: 100%;
		font-size: 13px;
		color: #DCB736;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.pas-r{
		width: 50%;
		height: 100%;
		font-size: 13px;
		color: red;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.bottom{
		width: 90%;
		height: 100px;
		/* background-color: #6641E2; */
		position: fixed;
		bottom: 0;
	}
	.bottom-u{
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.bottom-u-m{
		font-size: 12px;
		color: #DCB736;
	}
</style>
