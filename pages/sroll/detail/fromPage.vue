<template>
	<view>
		<page-head title="表单"></page-head>
		<view class="uni-padding-wrap">
			<form @submit="formSubmit" @reset="formReset">
				<view class="uni-form-item uni-column">
					<view class="title">开关(switch)</view>
					<view>
						<switch name="switch" />
					</view>
				</view>
				<view class="uni-form-item uni-column">
					<view class="title">单选(radio)</view>
					<radio-group name="radio">
						<label>
							<radio value="radio1" /><text>选项一</text>
						</label>
						<label>
							<radio value="radio2" /><text>选项二</text>
						</label>
					</radio-group>
				</view>
				<view class="uni-form-item uni-column">
					<view class="title">多选(多选)</view>
					<checkbox-group name="checkbox">
						<label>
							<checkbox value="checkbox1" /><text>选项一</text>
						</label>
						<label>
							<checkbox value="checkbox2" /><text>选项二</text>
						</label>
					</checkbox-group>
				</view>
				<view class="uni-form-item uni-column">	
					<view class="title">滑动条(slider)</view>
					<slider value="50" name="slider" show-value></slider>
				</view>
				<view class="uni-form-item uni-column">
					<view class="title">填写框(input)</view>
					<input class="uni-input" name="input" placeholder="输入框" />
				</view>
				<view class="uni-form-item uni-column">
					<view class="title">文本域(textarea)</view>
					<view class="uni-textarea">
						<textarea name="textarea" style="background-color: #ffffff;width: 100%;" placeholder="请输入内容"/>
					</view>
				</view>
				<view class="uni-btn-v">
					<button form-type="submit">提交</button>
					<button type="default" form-type="reset">重设</button>
				</view>
			</form>
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
			formSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
				var formdata = e.detail.value
				uni.showModal({
					content: '表单数据内容：' + JSON.stringify(formdata),
					showCancel: false
				});
			},
			formReset: function(e) {
				console.log('清空数据')
			}
		}
	}
</script>

<style>
	page {
	    background-color: #F4F5F6;
		height: 100%;
		width: 100%;
	}
</style>
