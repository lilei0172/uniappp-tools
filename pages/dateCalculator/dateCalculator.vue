<template>
	<view class="container">
		 <view class="date-card">
			<view class="flow-title">
				<text>计算日期差</text>
			</view>
			<view class="date-list">
				<view class="date-li">
					<view class="date-title">请选择开始日期</view>
					<picker mode="date" :value="startDate" :start="limitStartDate"
					:end="limitEndDate" @change="startDateChange">
						<view class="uni-input date-picker">{{startDate}}</view>
					</picker>
				</view>
				<view class="date-li">
					<view class="date-title">请选择结束日期</view>
					<picker mode="date" :value="endDate" :start="limitStartDate"
					:end="limitEndDate" @change="endDateChange">
						<view class="uni-input date-picker">{{endDate}}</view>
					</picker>
				</view>
				<text class="date-result">{{resultDate}}</text>
				
			</view>
		</view>
		<view class="date-card">
			<view class="flow-title">
				<text>计算日期</text>
			</view>
			<view class="date-list">
				<view class="date-li">
					<view class="date-title">请选择开始日期</view>
					<picker mode="date" :value="startDay" :start="limitStartDate"
					:end="limitEndDate" @change="startDayChange">
						<view class="uni-input date-picker">{{startDay}}</view>
					</picker>
				</view>
				<view class="date-li">
					<view class="date-title">请输入日期间隔(天)</view>
					<input type="number" v-model="dayInterval" placeholder="可以为负数">
				</view>
				<text class="date-result">{{resultDay}}</text>
				
			</view>
		</view>
		<view class="search-card">
			<view class="flow-title">
				<text>应用说明</text>
			</view>
			<view class="detial-list">
				<image src="../../static/img/dot.svg" mode=""></image>
				<text>日期格式: yyyy-MM-dd , 如 2020-02-02</text>
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
			const currentDate = this.getDate({
				format: true
			})
			return {
				resultDay:'resultDay',
				startDay: '点击选择',
				dayInterval:'',
				resultDate:'resultDate',
				startDate: '点击选择',
				endDate:'点击选择'
			}
		},
		onLoad(option) {
			uni.setNavigationBarTitle({
				title:'日期计算器'
			})
		},
		computed: {
			limitStartDate() {
				return this.getDate('start');
			},
			limitEndDate() {
				return this.getDate('end');
			}
		},
		methods: {
			gotoCopyright:function(){
				
			},
			startDateChange: function(e) {
				this.startDate = e.target.value;
				if(this.startDate !='点击选择'&&this.endDate!='点击选择'){
					this.getResultTimeStamp(this.startDate,this.endDate)
				}
			},
			endDateChange: function(e) {
				
				this.endDate = e.target.value;
				if(this.startDate !='点击选择'&&this.endDate!='点击选择'){
					this.getResultTimeStamp(this.startDate,this.endDate)
				}
			},
			startDayChange: function(e) {
				this.startDay = e.target.value;
				if(this.startDay !='点击选择'&&this.dayInterval!=''){
					
				}
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
	
				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
			getResultTimeStamp(start,end){
				let resultTimeStamp = new Date(end).valueOf()-new Date(start).valueOf();
				if(resultTimeStamp<0){
					this.resultDate = '开始日期应小于结束日期'
				}else{
					let resultDate = this.getResultDate(resultTimeStamp);
					this.resultDate = '约等于'+resultDate.day+'天'
				}
			},
			getResultDate(timeStamp){
				let day = (timeStamp/1000/60/60/24).toFixed(2); 
				return {
					day:day,
				}
			}
		}
	}
</script>

<style lang="scss">
	.date-card{
		position: relative;
		width: calc(100% - 100rpx);
		margin: 100rpx 20rpx 20rpx;
		padding: 20rpx 30rpx 50rpx 30rpx;
		border: 1px solid #ccc;
		border-top:1px solid #eee;
		border-radius: 20rpx;
		box-shadow: 0rpx 3rpx 3rpx #aaa ;
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
		.date-list{
			width: 100%;
			margin-top: 50rpx;
			.date-title{
				color:#666;
				font: normal normal 20rpx/30rpx "Arial","Microsoft YaHei","黑体","宋体",sans-serif;
			}
			.date-picker,input{
				margin: 10rpx 0 20rpx 0;
				border-bottom: 1rpx solid #ccc;
			}
			.date-result{
				display: block;
				width: 100%;
				height: 70rpx;
				margin: 10rpx 0;
				border: 1rpx solid #eee;
				
				font:normal normal 40rpx/70rpx "Arial","Microsoft YaHei","黑体","宋体",sans-serif;
			}
		}
	}
	.search-card{
		position: relative;
		width: calc(100% - 100rpx);
		margin: 100rpx 20rpx 20rpx;
		padding: 20rpx 30rpx 50rpx 30rpx;
		border: 1px solid #ccc;
		border-top:1px solid #eee;
		border-radius: 20rpx;
		box-shadow: 0rpx 3rpx 3rpx #aaa ;
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
