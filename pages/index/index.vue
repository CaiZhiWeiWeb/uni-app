<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<view class="">
			<button type="default" @click="chooseImage">上传图片</button>
		</view>
		<view class="">
			<p>
				<image v-for="(imgs,index) in imgArr" :src="imgs" :key="index" @click="preImage(imgs)" />
			</p>
		</view>
		<!-- #ifdef H5 -->
		<view>我是h5页面</view>

		<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<view>我是小程序页面</view>
		<!-- #endif -->
		<navigator url="/pages/message/message" open-type="switchTab">跳转</navigator>
		<button type="default" @click="toDetail">跳转至详情内页</button>
		<button type="default" @click="toBar">跳转到bar</button>
		<test :title="title" @update="up"></test>
	</view>
</template>

<script>
	import test from '../../components/test.vue'
	export default {
		data() {
			return {
				title: 'Hello1',
				imgArr: []
			}
		},
		onPullDownRefresh() {
			console.log('触发了下拉刷')
		},
		onLoad() {
		    
			console.log('页面加载了');
			uni.stopPullDownRefresh()
		},
		components:{
			test
		},
		methods: {
			chooseImage() {
				uni.chooseImage({
					count: 5,
					success: res => {
						this.imgArr = res.tempFilePaths
					}
				})
			},
			preImage(current) {
				console.log(current)
				uni.previewImage({
					current,
					urls: this.imgArr,
					loop: true,
					indicator: 'number'
				})
			},
			toDetail(){
				uni.navigateTo({
				   url:'/pages/detail/detail'
				})
			},
			toBar(){
				uni.switchTab({
					url:'/pages/message/message'
				})
			},
			up(val){
				console.log(val)
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
