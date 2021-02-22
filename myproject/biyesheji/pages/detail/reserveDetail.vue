<template>
<view style="positon:relative">
    <view class="back-icon" @click="getBackTo()"><text class="iconfont icon-fanhuijiantou"></text></view>
    <view class="reserve-detail">
        <view class="reserve-detail-title">
                <text style="color:#606060;font-size:36rpx;font-weight:bold">四姑娘山</text>
                <u-rate :disabled="true" :count="5" v-model="value"></u-rate>
            </view>
            <view class="reserve-detail-content">
                <text>四姑娘山以雄峻挺拔闻名,山体陡峭,直至蓝天,冰雪覆盖,银光照人。山麓森林茂密,绿草如茵,清澈的...</text>
            </view>
            <view class="reserve-detail-info">
                <text style="font-weight:bold;">游玩日期</text>
                <view style="display:flex;flex-direction: row; justify-content: space-between;margin-top:40rpx;">
                    <view :style="{background:select==index?'#E6F1FE':'', borderColor: select==index?'#48BBF0':'#D3D3D3'}" class="reserve-select-time" v-for="(item,index) in timeList" :key="index" @click="getSelected(index)">
                        <text>{{item.date}}:{{item.time}}</text>
                        <view class="reserve-select-price">
                                <text style="font-weight:bold;">{{item.price}}￥</text>
                                <text :style="{background:select==index?'#48BBF0':''}" style="color:#ffffff;border-radius:10rpx 0 20rpx 0 ;padding:6rpx;font-size:28rpx;" class="iconfont icon-biaodankongjiandanxuan"></text>
                        </view>
                    </view>
                    <view class="reserve-select-more" @click="getSelectDate">
                        <text class="iconfont icon-jinrujiantouxiao"></text>
                        <text >更多</text>
                    </view>
                </view>
                        <u-calendar :min-date="dayTime" :max-date="'2060-01-01'" v-model="show" :start-text="'77元'" :mode="mode" @change="change">
                            
                        </u-calendar>
                <view class="reserve-select-num">
                    <text>购买数量（此单限购五张）</text>
                <u-number-box :min="1" :max="5" v-model="number" @change="valChange"></u-number-box>
                
                </view>
            </view>
           
    </view>
    <view class="reserve-userInfo">
        <text style="font-weight:bold;">游客信息</text>
        <view class="reserve-userInfo-input">
            <text style="margin-right:30rpx;">游客姓名:</text>
            <input type="text" placeholder="必填，输入证件上的姓名">
        </view>
        <view class="reserve-userInfo-input">
            <text style="margin-right:30rpx;">电话号码:</text>
            <input type="text" maxlength="11" placeholder="必填，输入联系人号码">
        </view>
    </view>
    <view class="page-reserve">
        <u-button :custom-style="customStyle" :ripple="'true'" :shape="'circle'"  :hair-line="false" :type="'error'">确定预约并支付</u-button>
    </view>
</view>
</template>
<script>
import dayjs from 'dayjs' 
export default {
    data(){
        return{
            value:4.5,
            number:1,
            show: false,
            mode: 'date',
            select:0,
            timeList:[{
                date:'今天',
                time:'02-03',
                price:'77'
            },{
                date:'明天',
                time:'02-03',
                price:'77'
            },{
                date:'后天',
                time:'02-03',
                price:'77'
            }],
            dayTime:'',
            monthTime:''
        }
    },
    onLoad(){
        this.dayTime=dayjs().format('YYYY-MM-DD')
        this.monthTime=dayjs().format('MM-DD')
        let tomorrow =dayjs().add(1, 'day').format('MM-DD')
        let afterDay=dayjs().add(2, 'day').format('MM-DD')
        this.timeList[0].time= this.monthTime
        this.timeList[1].time=tomorrow
        this.timeList[2].time=afterDay
    },
    methods: {
        change(e) {
            console.log(dayjs().format('YYYY-MM-DD'));
            if(e.month<10){
                e.month='0'+e.month
            }
            if(e.day<10){
                e.day='0'+e.day
            }
            let list=e.week.split('')
            
            e.week='周'+list[2]
            console.log(e)
           
           this.timeList[2].time=e.month+'-'+e.day
           this.timeList[2].date=e.week
           this.select=2
        },
        getSelectDate(){
            this.show=true
        },
        getSelected(index){
            this.select=index
        },
        valChange(e){
            console.log(e)
        }
    }
}
</script>
<style>
.reserve-detail{
    width: 686rpx;
    margin: 0 auto;
    border-radius: 20rpx;
    background: #ffffff;
    display: flex;
    flex-direction: column;
    padding: 26rpx 34rpx 26rpx 34rpx;
    box-shadow: 0rpx 10rpx 18rpx 2rpx rgba(81, 79, 80, 0.2);
    margin-top: 140rpx;
}
.reserve-detail-title{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    
}
.reserve-detail-content{
    margin-top: 26rpx;
    padding-bottom: 31rpx;
    border-bottom: 2rpx solid#D3D3D3;
    color: #606060;
}
.back-icon{
    width: 52rpx;
    height: 52rpx;
    position: absolute;
    top: 50rpx;
    left: 30rpx;
    padding-left: 15rpx;
    border-radius: 52rpx;
    background: #000;
    opacity: 0.5;
    text-align: center;
    line-height: 52rpx;
    color: #ffffff;
}

.reserve-detail-info{
   
    display: flex;
    flex-direction: column;
    color: #606060;
    margin-top: 32rpx;
  
}
.reserve-select-time{
    display: flex;
    flex-direction: column;
    border: 3rpx solid #D3D3D3;/*#48BBF0*/
    border-radius: 20rpx;
    padding: 18rpx 0 0 10rpx;
    /* background: #E6F1FE; */
}
.reserve-select-price{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-top: 26rpx;
}
.reserve-select-more{
    display: flex;
    flex-direction: column;
    border: 3rpx solid #D3D3D3;
    border-radius: 20rpx;
    justify-content: center;
    padding: 0 8rpx 0 8rpx;
}
.reserve-select-num{
    margin-top: 80rpx;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
.reserve-userInfo{
    width: 686rpx;
    margin: 0 auto;
    background: #ffffff;
    display: flex;
    flex-direction: column;
    padding: 26rpx 34rpx 26rpx 34rpx;
    box-shadow: 0rpx 10rpx 18rpx 2rpx rgba(81, 79, 80, 0.2);
    margin-top: 32rpx;
    border-radius: 20rpx;
    color: #606060;
}
.reserve-userInfo-input{
    display: flex;
    flex-direction: row;
    border-top: 2rpx solid #D3D3D3;
    margin-top: 22rpx;
    padding-top: 40rpx;
    
}
.page-reserve{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 70rpx;
}
</style>