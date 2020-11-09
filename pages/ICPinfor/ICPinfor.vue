<template>
	<view class="container">
		<view class="search-card">
			<view class="search-title">
				<text>请输入待查询域名</text>
			</view>
			<view class="search-input">
				<input type="text" :value="searchInfor" 
				placeholder="Example: ccreed.com" confirm-type="search" />
			</view>
			
		</view>
		<view class="search-card">
			<view class="flow-title">
				<text>应用说明</text>
			</view>
			<view class="detial-list">
				<image src="../../static/img/dot.svg" mode=""></image>
				<text>可备案域名列表，请参考工信部可备案域名列表</text>
			</view>
		</view>
		<view class="copyright">
			<text space="nbsp">
				© 2016~2020 
				<h5 class="copyright-link" @tap="gotoCopyright()">
					LiLei®
				</h5> 
				 All rights reserved
			</text>
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchInfor:''
			}
		},
		onLoad(option) {
			uni.setNavigationBarTitle({
				title:'ICP备案查询'
			})
		},
		methods: {
			gotoCopyright:function(){
				
			}
		}
	}
</script>

<style lang="scss">
	.search-card{
		position: relative;
		width: calc(100% - 100rpx);
		margin: 20rpx 20rpx 100rpx;
		padding: 20rpx 30rpx 50rpx 30rpx;
		border: 1px solid #ccc;
		border-top:1px solid #eee;
		border-radius: 20rpx;
		box-shadow: 0rpx 3rpx 3rpx #aaa ;
		.search-title{
			padding-bottom: 30rpx;
			font: normal normal 45rpx/80rpx "Arial","Microsoft YaHei","黑体","宋体",sans-serif;
		}
		.search-input input{
			width: calc(100% - 20rpx);
			height: 80rpx;
			padding: 0 10rpx;
			border: 1rpx solid #ccc;
			border-radius: 10rpx;
		}
		.flow-title{
			position: absolute;
			top:-40rpx;
			width: 200rpx;
			height: 80rpx;
			padding: 0 15rpx;
			border-radius:20rpx;
			box-shadow: 0rpx 3rpx 3rpx #aaa ;
			background-color: #82b1ff;
			color: white;
			text-align: center;
			font: bolder normal 40rpx/80rpx "Arial","Microsoft YaHei","黑体","宋体",sans-serif;
		}
		.detial-list{
			margin-top: 40rpx;
			font: normal normal 35rpx/50rpx "Arial","Microsoft YaHei","黑体","宋体",sans-serif;
			image{
				height: 30rpx;
				width: 30rpx;
				margin-right: 10rpx;
			}
		}
	}
</style>
