<template>
	<view class="content">

		<view style="height: 1px;margin-top: 50px;"></view>
		<view class="row">
			<view class="row-l">昵称</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入手机号码" />
			</view>
		</view>

		<view style="height: 1px;margin-top: 10px;"></view>
		<view class="row">
			<view class="row-l">手机号码</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入手机号码" />
			</view>
		</view>
		<view class="code">
			<view class="code-i" v-if="show" @tap="code">
				获取验证码
			</view>
			<view class="code-i" v-else>
				{{msg}}
			</view>
		</view>


		<view style="height: 1px;margin-top: 10px;"></view>
		<view class="row">
			<view class="row-l">验证码</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入手机号码" />
			</view>
		</view>

		<view style="height: 1px;margin-top: 10px;"></view>
		<view class="row">
			<view class="row-l">邮箱</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入手机号码" />
			</view>
		</view>

		<view style="height: 1px;margin-top: 10px;"></view>
		<view class="row">
			<view class="row-l">真实姓名</view>
			<view class="row-r">
				<input type="number" style="font-size: 15px;" placeholder="请输入手机号码" />
			</view>
		</view>



		<view style="height: 1px;margin-top: 10px;"></view>
		<view>
			<checkbox color="#DCB736" style="color: #DCB736;">同意《用户服务协议》</checkbox>
		</view>

		<view style="height: 1px;margin-top: 10px;"></view>
		<view>
			<button class="login">立即注册</button>
		</view>



	</view>
</template>




<script>
	export default {
		data() {
			return {
				msg: "获取验证码",
				show: true
			}
		},
		methods: {
			code: function() {
				var second = 5
				this.show = false
				var interval = setInterval(() => {
					console.log(second)
					this.msg = "倒计时" + second
					if(second == 0){
						console.log("sss")
						this.show = true
					}
					second--
				var second = 5;
				this.msg = "倒计时" + second
				this.show = false
				var interval = setInterval(() => {
					this.msg = "倒计时" + --second
					if (second == 0) {
						this.show = true
					}
				}, 1000)
				setTimeout(() => {
					clearInterval(interval)
				}, 3000)


				}, 5010)

			},
		},

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

	.code {
		width: 100%;
		height: 25px;
		display: flex;
		justify-content: flex-end;
	}

	.code-i {
		width: 90px;
		height: 25px;
		font-size: 13px;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 1px solid #6641E2;
		color: #FF0000;
	}

	.mask {

		z-index: 999;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, 0.4);

	}
</style>
