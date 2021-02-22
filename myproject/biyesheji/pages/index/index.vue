<template>

	<view class="page">
		<view class="page-head" style="background: url(https://img.pic88.com/preview/2020/10/09/16022423075f804703d7c9b.jpg!s640) no-repeat;background-size: cover;">
			<view class="page-head-cotent">
				<view class="page-city">
					<text style="color: #ffffff; font-size: 32rpx;">成都</text>
					<text style="color: #ffffff;margin-left: 10rpx;" class="iconfont icon-xialajiantouxiao"></text>
				</view>
				<view class="page-input">
					<!-- <text style="font-size: 40rpx;"  class="iconfont icon-sousuo"></text> -->
					<input class="page-input-sty" type="text" placeholder="请输入你想查询的内容"/>
				</view>
			</view>
			<view class="page-guide">
				<u-swiper :list="list" :height="'420'" duration="3000" :circular="false"></u-swiper>
			</view>
			<view class="page-icon">
				<view class="page-icon-content">
				<view class="page-icon-sty" style="background: #F25359;"> 
					<text style="font-size: 80rpx;" class="iconfont icon-dujia"></text>
				</view>
				<text  style="margin-top: 10rpx;">热门景点</text>
				</view>
				<view class="page-icon-content">
					<view class="page-icon-sty" style="background: #64D555"> 
						<text style="font-size: 80rpx;" class="iconfont icon-guojijipiao"></text>
					</view>
					<text  style="margin-top: 10rpx;">精品路线</text>
				</view>
				<view class="page-icon-content">
					<view class="page-icon-sty" style="background: #FFBE4F;"> 
						<text style="font-size: 80rpx;" class="iconfont icon-guojijiudian"></text>
					</view>
					<text style="margin-top: 10rpx;">酒店民宿</text>
				</view>
				<view class="page-icon-content">
					<view class="page-icon-sty" style="background: #44A7FE"> 
						<text style="font-size: 80rpx;" class="iconfont icon-youji"></text>
					</view>
					<text  style="margin-top: 10rpx;">攻略</text>
				</view>
			</view>
			<view class="page-tag">
				<image class="page-tag-img" :src="testTagPic"></image>
			</view>
			<view class="page-hot">
				<view class="page-hot-title">
					<text style="font-size: 36rpx;">热门景点</text>
					<view class="page-font-more">
						<text style="margin-right: 10rpx;">更多 </text>
						<text style="font-size: 15rpx;align-items: center;"  class="iconfont icon-bofang"></text>
					</view>
				</view>
				<view class="page-hot-content">
					<view class="page-hot-pos" v-for="(item,index) in hotList" :key="index">
						<image style="width: 192rpx;height: 192rpx;border-radius: 14rpx;" :src="item.src"></image>
						<text class="page-hot-text">{{item.name}}</text>
					</view>
				</view>
			</view>
			<view class="page-recommend">
				<view class="page-hot-title">
					<text style="font-size: 36rpx;font-weight: 600;">热门推荐</text>
					<view class="page-font-more">
						<text style="margin-right: 10rpx;font-weight: 600;">更多 </text>
						<text style="font-size: 15rpx;align-items: center;"  class="iconfont icon-bofang"></text>
					</view>
				</view>
				<view class="page-recommend-pos">
					<view  class="page-recommend-content" v-for="(item,index) in recommendList" :key="index" @click="getToDetail">
						<image style="width: 192rpx;height: 192rpx;border-radius: 14rpx;margin-right: 30rpx;"  :src="item.src"></image>
						<view class="page-recommend-info">
							<text style="font-size: 35rpx;margin-bottom: 22rpx;">{{item.name}}</text>
							<text style="width: 380rpx;height: 70rpx;overflow: hidden;text-overflow:ellipsis;white-space: wrap;">{{item.detail}}</text>
							<view class="page-recommend-detail">
								<text>推荐指数：</text><u-rate :disabled="true" :count="item.count" v-model="item.value"></u-rate>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [{
						image: '/static/image/testPic.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://img.pic88.com/preview/2020/10/09/16021786075f7f4e2f0db8f.jpg!s640',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://img.pic88.com/preview/2020/10/07/16020665105f7d984e081c8.jpg!s640',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
					}
				],
				testTagPic:'../../static/image/testTagPic.png',
				hotList:[{
					src:'https://img.pic88.com/preview/2020/10/09/16021786075f7f4e2f0db8f.jpg!s640',
					name:'九皇山'
				},{
					src:'https://img.pic88.com/preview/2020/10/07/16020665105f7d984e081c8.jpg!s640',
					name:'千佛山'
				},{
					src:'https://img.pic88.com/preview/2020/10/08/16021243845f7e7a60bca8c.jpg!s640',
					name:'仙海湖'
				}],
				recommendList:[{
					src:'https://img.pic88.com/preview/2020/10/06/16019885145f7c67a29a89f.jpg!s640',
					name:'仙海湖',
					detail:'仙海风景区水质优良，湖面宽广，植被繁茂，地形地貌奇特 。 ',
					count:5,
					value:5
				},{
					src:'https://img.pic88.com/preview/2020/10/06/16019885145f7c67a29a89f.jpg!s640',
					name:'仙海湖',
					detail:'仙海风景区水质优良，湖面宽广，植被繁茂，地形地貌奇特 。',
					count:5,
					value:4
				},{
					src:'https://img.pic88.com/preview/2020/10/06/16019885145f7c67a29a89f.jpg!s640',
					name:'仙海湖',
					detail:'仙海风景区水质优良，湖面宽广，植被繁茂，地形地貌奇特 。',
					count:5,
					value:3
				},{
					src:'https://img.pic88.com/preview/2020/10/06/16019885145f7c67a29a89f.jpg!s640',
					name:'仙海湖',
					detail:'仙海风景区水质优良，湖面宽广，植被繁茂，地形地貌奇特 。',
					count:5,
					value:5
				}],
				
			}
			
		},
		methods:{
			getToDetail(){
				uni.navigateTo({	
					 url: '/pages/detail/detail'
				});
				
			}
		}
		
	}
</script>

<style>
.page{
	display: flex;
	flex-direction: column;
	background: #F3F4FB;
}
.page-head{
	display: flex;
	flex-direction: column;
	width: 100%;
	height: 680rpx;
	
	background-size: cover;
}

.page-head-cotent{
	display: flex;
	flex-direction: row;

}
.page-input-sty{
	width: 350rpx;
	height: 55rpx;
	font-size: 26rpx;
	color: #606060;
	border-radius: 59rpx;
	padding-left: 60rpx;
	background: url(../../static/image/search.png) no-repeat ;
	background-color: #ffffff;
	background-size: 40rpx;
	background-position: 10rpx 10rpx;
}
.page-input{
	display: flex;
	flex-direction: row;
	margin-top: 50rpx;
	margin-left: 25rpx;

}
.page-city{
	margin-top: 50rpx;
	margin-left: 40rpx;
	font-family: SourceHanSansCN-Bold;
	font-weight: bold;
}
.page-guide{
	width: 686rpx;
	height: 420rpx;
	background: #ffffff;
	margin: 0 auto;
	margin-top: 50rpx;
	border-radius: 20rpx;

}
.page-icon{
	width: 686rpx;
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	color: #606060;
	font-weight: 600;
	text-align: center;
	margin: 0 auto;
	margin-top: 50rpx;
}
.page-icon-sty{
	color: #ffffff;
	width: 120rpx;
	height: 120rpx;
	border-radius: 120rpx;
	box-shadow: 10rpx;
	text-align: center;
	line-height: 120rpx;
	
}

.page-icon-content{
	display: flex;
	flex-direction: column;
	justify-content: center;
}
.page-tag{
	margin: 0 auto;
	margin-top: 54rpx;
	
}
.page-tag-img{
	width: 686rpx;
	height: 208rpx;
	border-radius: 20rpx
}
.page-hot{
	width: 686rpx;
	margin: 0 auto;
	color: #606060;
	font-weight: 600;
	margin-top: 55rpx;
}
.page-hot-title{
	display: flex;
	flex-direction: row;
	justify-content: space-between;
}
.page-font-more{
	display: flex;
	justify-content: center;
	align-items: center;
	color: #8e8e8e;
}
.page-hot-content{
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	margin-top: 56rpx;
}
.page-hot-pos{
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}
.page-hot-text{
	width: 160rpx;
	height: 60rpx;
	line-height: 60rpx;
	background: #ffffff;
	text-align: center;
	margin-top: -30rpx;
	border-radius: 60rpx;
	box-shadow: 0rpx 10rpx 18rpx 2rpx rgba(81, 79, 80, 0.2);
}
.page-recommend{
	width: 686rpx;
	margin: 0 auto;
	margin-top: 55rpx;
	display: flex;
	flex-direction: column;
	color: #606060;
	
}
.page-recommend-pos{
	margin-top: 33rpx;
}
.page-recommend-content{
	display: flex;
	flex-direction: row;
	margin-bottom: 29rpx;
	background: #ffffff;
	border-radius: 10rpx;
	/* border: 2rpx solid red; */
	padding:16rpx 13rpx 16rpx 13rpx;	
	box-shadow: 0rpx 0rpx 18rpx 2rpx rgba(81, 79, 80, 0.2);	
}
.page-recommend-info{
	display: flex;
	flex-direction: column;
	
}
.page-recommend-detail{
	margin-top: 20rpx;
}
</style>
