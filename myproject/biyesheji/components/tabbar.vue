<template>
    <view>
        <u-tabbar v-model="current" :list="list" :mid-button="true"></u-tabbar>
    </view>
</template>
<script>
export default {
    data(){
        return {
            tabList: [{
						iconPath: "home",
						selectedIconPath: "home-fill",
						text: '首页',
						count: 2,
						isDot: true,
						customIcon: false,
					},
					{
						iconPath: "photo",
						selectedIconPath: "photo-fill",
						text: '放映厅',
						customIcon: false,
					},{
						iconPath: "photo",
						selectedIconPath: "photo-fill",
						text: '放映厅',
						customIcon: false,
					}],
                    current: 0
        }
    }
}
</script>