
# [github地址](https://github.com/LiYaMei94/uniApp_card_page_turning)
# SJ-CardPageTurning
## SJ-CardPageTurning组件参数说明
|参数| 类型 |默认值
|--|--|--|
| card_data | Array |（详细信息如下所示）
### card_data详情

```javascript
card_data:[
	{
		img: '../../static/SJ-CardPageTurning/card_img/card1.jpg',
		anim: null,
		like_state: 0//-1：左滑，0：没滑动，1：右滑
	},
	{
		img: '../../static/SJ-CardPageTurning/card_img/card2.jpg',
		anim: null,
		like_state: 0//-1：左滑，0：没滑动，1：右滑
	},
	{
		img: '../../static/SJ-CardPageTurning/card_img/card4.jpg',
		anim: null,
		like_state: 0//-1：左滑，0：没滑动，1：右滑
	},
	{
		img: '../../static/SJ-CardPageTurning/card_img/card5.jpg',
		anim: null,
		like_state: 0//-1：左滑，0：没滑动，1：右滑
	}
]
```



## scss文件参数

```scss
$card_width: 600upx; //卡片的宽度
$card_height: 1000upx; //卡片的高度
$card_borderRadius_size:10upx;//卡片的圆角大小

$card_isLikeBg_size:100upx;//喜欢和不喜欢的图标背景大小
$card_isLikeBg_bgColor:#d81e06;//喜欢和不喜欢的图标背景颜色
$card_isLikeBg_spacing:25upx;//喜欢和不喜欢的图标距上边距和距左、距右边距的距离
$card_isLikeImg_size:50upx;//喜欢和不喜欢的图标大小
```

## 使用方式

```javascript
<template>
	<view class="content">
		<CardPageTurning ></CardPageTurning>
	</view>
</template>

<script>
import CardPageTurning from '../../components/SJ-CardPageTurning/SJ-CardPageTurning.vue';
export default {
	components:{
		CardPageTurning
	},
	data() {
		return {
			
		};
	},
	onLoad() {
		
	},
	methods: {
		
		
	}
};
</script>

<style scoped>
.content {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	padding-top: 100upx;
	box-sizing: border-box;
}

</style>

```
# 适应PC端
新建一个js文件，文件内容如下所示，然后在main.js文件中引入即可使用。
```javascript
(function (){
	var u = navigator.userAgent,
		w = window.innerWidth;
	if (!u.match(/AppleWebKit.*Mobile.*/) || u.indexOf('iPad') > -1) {
		var sw = w*576/1920;
		window.innerWidth = sw<375?375:sw;
                window.onload = function() {
		        window.innerWidth = w;
	        }
	}
})();
```

```javascript
import pc from './utils/pc.js'
import Vue from 'vue'
import App from './App'

Vue.config.productionTip = false

App.mpType = 'app'

const app = new Vue({
    ...App
})
app.$mount()

```

# 注意：
- 在运行到小程序开发工具时请把main.js中的import pc from './utils/pc.js'注释掉
- 我使用的是scss，如果没有安装scss，请务必将组件中的lang改为css，并引入@import './SJ-CardPageTurning.css';
