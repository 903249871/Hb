<template>
	<view class="content">
		<view class="login-from">
			<view class="logo"><image src="../../static/eka.jpg"></image></view>
			<view class="uni-form-item uni-column" >
				<input type="text" class="uni-input" name="input" placeholder="请输入账号" @input="userNameInpur" />
			</view>
			<view class="uni-form-item uni-column" >
				<input class="uni-input" password="true" name="input" placeholder="请输入密码" @input="passwordInpur" />
			</view>
			<view class="loginBtn">
				<button type="primary" plain="true" @tap="login">登录</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userName: ""
				,password: ""
			}
		},
		onLoad() {
	
		},
		methods: {
			userNameInpur(e){
				this.userName = e.detail.value
			},
			passwordInpur(e){
				this.password = e.detail.value
			},
			login(){
				uni.showLoading({
				    title: '正在登录'
				});
				if(this.password===""||this.userName===""){
					uni.hideLoading();
					uni.showModal({
						title: '提示',
						content: '请先输入账号和密码！',
						showCancel: false,
						success: function (res) {
							if (res.confirm) { //确定
							} else if (res.cancel) {
							}
						}
					});
					return false;
				}
				setTimeout(()=>{ //模拟请求
					//方法体
					uni.hideLoading();
					if(this.password!="123"){
						uni.showModal({
							title: '提示',
							content: '登录失败，请检查账号密码是否正确？',
							showCancel: false,
							success: function (res) {
								if (res.confirm) { //确定
								} else if (res.cancel) {
								}
							}
						});
					}else{
						uni.switchTab({
							url: '/pages/sroll/srollPage'
						});
					}
					//end方法体
				}, 1500);
			}
		},
	}
</script>

<style>
	page {
	    background-color: #F4F5F6;
		height: 100%;
		width: 100%;
	}
	.content{
		height: 100%;
		width: 100%;
		display:-webkit-flex;
		display:flex;
		flex-flow: column wrap;/*替代上面两行*/
		justify-content: center;
		align-items: center;/*垂直居中*/
	}
	
	.login-from{
		height: 50%;
		width: 80%;
		display:-webkit-flex;
		display:flex;
/* 		flex-direction: column;
		flex-wrap: wrap; */
		flex-flow: column wrap;/*替代上面两行*/
		justify-content: space-between;
		align-items: center;/*垂直居中*/
		margin-bottom: 150upx;
	}
	.logo image{
		height: 150upx;
		width: 400upx;
	}
	.loginBtn {
		width: 80%;
	}
</style>
