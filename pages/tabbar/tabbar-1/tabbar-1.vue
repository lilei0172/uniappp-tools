<template>
	<view class="content">
		<view class="toolBox">
			<view class="toolTitle">
				日常工具
			</view>
			<view class="toolBtnBox">
				<button class="toolBtn" v-for="item in ">ICP备案查询</button>
				<button class="toolBtn">日期计算器</button>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			title: 'Hello',
			toolBtnList:{
				0:{
				name:"日常工具",
				itemlist:{
					0:"ICP备案查询",
					1:"日期计算器",
					2:"抽象话生成",
					3:"亲戚关系计算",
					4:"网速测试"
				},
				}
			}
		};
	},
	onLoad() {},
	methods: {}
};
</script>

<style lang="scss">
.content {
	
}
.toolBox{
	width: calc(100% - 60rpx);
	padding: 20rpx 30rpx;
	.toolTitle{
		width: 100%;
		height: 80rpx;
		font: normal normal 60rpx/100% Tahoma;
		color:#333;
	}
	.toolBtnBox{
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: center;
		.toolBtn{
			height: 80rpx;
			width: 45%;
			margin: 10rpx 0;
			border: none !important;
			border-radius: 0rpx !important;
			font: normal normal 30rpx/80rpx Tahoma;
			color:#333;
			
		}
		& .toolBtn:nth-child(2n+1){
			margin-right: 10%;
		}
	}
}
input{
	width: 500rpx;
	border: 1rpx solid gray;
	border-radius: 5rpx;
	cursor: pointer;
}
</style>
