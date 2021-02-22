<template>
<view style="positon:relative">
    <view class="back-icon" @click="getBackTo()"><text class="iconfont icon-fanhuijiantou"></text></view>
    <view class="page">
       
        <!-- <u-swiper class="page-image" :height="556" :list="list"></u-swiper> -->
        <image class="page-image" :src="src"></image>
        <mid-detail style="margin-top:-50rpx;margin-bottom: 28rpx;"></mid-detail>
        <view class="page-ticket">
            <view class="page-ticket-title">
                <text>门票</text>
            </view>
            <view class="page-ticket-price" v-for="(item,index) in priceList" :key="index">
                <text>{{item.name}}</text>
                <text class="page-ticket-price-sty">{{item.price}}元/人</text>
            </view>
            
        </view>
        <view class="page-appraise">
            <view class="page-appraise-title">
                <text>用户评价</text>
            </view>
             <view class="page-appraise-content"><!--/*这里的评价需要循环 */ -->
                <view class="page-appraise-content-head">
                    <view class="page-appraise-cotent-username">
                        <text style="margin-right:20rpx">李*龙</text>
                        <text>2021-02-07</text>
                    </view>
                    <u-rate :disabled="true" :count="5" v-model="value"></u-rate>
                </view>
                <view class="page-appraise-info">
                    <text>午晒成🐶，大本营真没信号，刚回来，队友们都去封顶了，我负责垫底，其四姑娘山二峰大本营这儿海拔4200左右，晚上冻成🐶 ，中午晒成🐶，大本营真没信号，刚回来，队友们都去封顶了，我负责垫底，其四姑娘山二峰大本营这儿海拔4200左右，晚上冻成🐶 ，中午晒成🐶，大本营真没信号，刚回来，队友们都去封顶了，我负责垫底，其四姑娘山二峰大本营这儿海拔4200左右，晚上冻成🐶 ，中午晒成🐶，大本营真没信号，刚回来，队友们都去封顶了，我负责垫底，其</text>
                </view>
            </view>
        </view>
        <view class="page-reserve">
            <u-button :custom-style="customStyle" :ripple="'true'" :shape="'circle'" :size="'medium'" :hair-line="false" :type="'primary'">预定门票</u-button>
        </view>
    </view>
    </view>
</template>
<script>
import midDetail from '../detail/components/midDetail'
export default {
    components:{
        midDetail
    },
    data(){
        return {
            src:'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.ewebweb.com%2Fuploads%2F20190623%2F21%2F1561296892-xIqoiKBbNU.jpg&refer=http%3A%2F%2Fimg.ewebweb.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1616393999&t=0ce3dfb7e39e33b48db51acf6e9d1a1b',
            priceList:[{
                name:'成人票',
                price:'78'
            },{
                name:'儿童票',
                price:'36'
            },{
                name:'学生票',
                price:'36'
            }],
            value:5,
            customStyle:{
                background:'#6767F7',
                width:'380rpx',
                marginTop:'40rpx',
                marginBottom:'46rpx'
            }
        }
    },
    methods:{
        getBackTo(){
            uni.navigateBack({
                 delta: 2
            });
        }
    }
    
}
</script>
<style>
.page{
    display: flex;
    flex-direction: column;
    background: #F4F4F8;
    align-items: center;
   
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
.page-image{
    width: 750rpx;
    height: 556rpx;
}
.page-ticket{
    width: 686rpx;
    margin:  0 auto;
    border-radius: 20rpx;
    background: #ffffff;
    padding: 26rpx 34rpx 26rpx 34rpx;
    box-shadow: 0rpx 10rpx 18rpx 2rpx rgba(81, 79, 80, 0.2);
    display: flex;
    flex-direction: column;
}
.page-ticket-title{
    color: #606060;
    border-bottom: 2rpx solid#D3D3D3;
    padding-bottom: 24rpx;
    font-size:36rpx;
    font-weight:bold;
}
.page-ticket-price{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-top: 28rpx;
    color: #606060;
    font-weight: bold;
}
.page-ticket-price-sty{
    background:  #6767F7;
    padding: 10rpx 40rpx 10rpx 40rpx;
    border-radius: 30rpx;
    color: #ffffff;
}
.page-appraise{
    display: flex;
    flex-direction: column;
    width: 686rpx;
    margin:  0 auto;
    border-radius: 20rpx;
    background: #ffffff;
    padding: 26rpx 34rpx 26rpx 34rpx;
    box-shadow: 0rpx 10rpx 18rpx 2rpx rgba(81, 79, 80, 0.2);
    margin-top: 30rpx;
}
.page-appraise-title{
    color: #606060;
    font-size:36rpx;
    font-weight:bold;
}
.page-appraise-content{
    display: flex;
    flex-direction: column;
    margin-top: 29rpx;
    color: #606060;
    border-top: 2rpx solid#D3D3D3;
    padding-top: 24rpx;
}
.page-appraise-content-head{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
.page-appraise-cotent-username{
    color: #606060;
}
.page-appraise-info{
    margin-top: 30rpx;
   color: #606060;
   font-size: 22rpx;
   display: -webkit-box;
   -webkit-box-orient: vertical;
   -webkit-line-clamp: 4;
   overflow: hidden;
  
}

</style>