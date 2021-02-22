<template>
    <view class="detail">
        <view class="detail-title">
            <text style="color:#606060;font-size:36rpx;font-weight:bold">四姑娘山</text>
            <u-rate :disabled="true" :count="5" v-model="value"></u-rate>
        </view>
        <view class="detail-content">
            <text>四姑娘山以雄峻挺拔闻名,山体陡峭,直至蓝天,冰雪覆盖,银光照人。山麓森林茂密,绿草如茵,清澈的...</text>
        </view>
        <view class="detail-time">
            <text class="detail-time-sty">正在营业</text>
            <text>08:30 - 17:00</text>
        </view>
        <view class="detail-info">
            <text>特色：风景漂亮、骑马、天然氧吧</text>
        </view>
        <view class="detail-location">
            <text style="  width: 480rpx;">四川省阿坝藏族羌族自治州小金县四姑娘山镇</text>
            <view class="detail-guide"><text class="iconfont icon-daohang"></text>导航</view>
        </view>
    </view>
</template>
<script>
export default {
    data(){
        return{
            value:4.5
        }
    }
}
</script>
<style>
.detail{
    width: 686rpx;
    margin: 0 auto;
    border-radius: 20rpx;
    background: #ffffff;
    display: flex;
    flex-direction: column;
    padding: 26rpx 34rpx 26rpx 34rpx;
    box-shadow: 0rpx 10rpx 18rpx 2rpx rgba(81, 79, 80, 0.2);
}
.detail-title{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    
}
.detail-content{
    margin-top: 26rpx;
    padding-bottom: 31rpx;
    border-bottom: 2rpx solid#D3D3D3;
    color: #606060;
}
.detail-time{
    display: flex;
    flex-direction: row;
    color: #606060;
    font-weight: bold;
    margin-top: 24rpx;
    padding-bottom: 24rpx;
    border-bottom: 2rpx solid#D3D3D3;
}
.detail-time-sty{
    font-size: 22rpx;
    line-height: 22rpx;
    color: #6767F7;
    background: #E2E2FF;
    border-radius: 22rpx;
    padding: 9rpx 18rpx 9rpx 18rpx;
    font-weight: normal;
    margin-right: 20rpx;
}
.detail-info{
    color: #606060;
    margin-top: 24rpx;
    padding-bottom: 24rpx;
    border-bottom: 2rpx solid#D3D3D3;
}
.detail-location{
  
    font-size: 24rpx;
    margin-top: 24rpx;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
}
.detail-guide{
    font-size: 26rpx;
    font-weight: bold;
    color: #6767F7;
    background: #F4F4F8;
    border-radius: 22rpx;
    padding: 10rpx 26rpx 10rpx 26rpx;
}
.detail-guide:active{
    color:#F4F4F8;
    background: #6767F7;;
}
</style>