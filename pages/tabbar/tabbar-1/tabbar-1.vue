<template>
	<view class="content">
		<view class="toolBox" v-for="item,index in toolBtnList">
			<view class="toolTitle">
				<icon class="iconfont" :class="item.icon"></icon>
				<text>{{item.name}}</text>
			</view>
			<view class="toolBtnBox">
				<button class="toolBtn" v-for="item,index in item.itemlist" 
				:data-newsid="item.url" @tap="openinfo($event)">{{item.title}}</button>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			isActive:'#e2e2e2',
			title: 'Hello',
			toolBtnList:{
				0:{
				name:"日常工具",
				icon:'icon-rili',
				itemlist:{
					0:{
						title:"ICP备案查询",
						url:"ICPinfor"
					},
					1:{
						title:"日期计算器",
						url:"dateCalculator"
					},
					2:{
						title:"抽象话生成",
						url:""
					},
					3:{
						title:"亲戚关系计算",
						url:""
					},
					
				}
				},
				1:{
				name:"极客工具",
				icon:'icon-gongju',
				itemlist:{
					0:{
						title:"网页源码查看",
						url:""
					},
					1:{
						title:"Base64转换",
						url:""
					},
					2:{
						title:"UserAgent解析",
						url:""
					},
					3:{
						title:"全球IP查询",
						url:""
					},
					
				},
				},
				2:{
				name:"文本工具",
				icon:'icon-wenbenbianji',
				itemlist:{
					0:{
						title:"数字中文互转",
						url:""
					},
					1:{
						title:"富文本编辑器",
						url:""
					},
					2:{
						title:"汉语转拼音",
						url:""
					},
					3:{
						title:"摩斯电码",
						url:""
					},
					
				},
				}
			}
		};
	},
	onLoad() {},
	methods: {
		openinfo(e) {
			var newsid = e.currentTarget.dataset.newsid;
			console.log(e,newsid)
			
			uni.navigateTo({
			    url: '../../'+newsid+'/'+newsid
			});
		}
	}
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
		justify-content: center;
		color:#333;
		text{
			font: normal normal 50rpx/80rpx Tahoma;
		}
		icon{
			
			margin-right: 20rpx;
		}
	}
	.toolBtnBox{
		width: 100%;
		display: flex;
		flex-direction: row;
		 flex-wrap:wrap;
		justify-content: left;
		.toolBtn{
			height: 80rpx;
			width: 45%;
			margin: 10rpx 0;
			border: none ;
			border-radius: 10rpx ;
			
			text-align: center;
			font: normal normal 30rpx/80rpx Tahoma;
			
			
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
