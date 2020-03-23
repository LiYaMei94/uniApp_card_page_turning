<template>
	<view class="card_wrap">
		<view
			class="card_item"
			v-for="(item, index) in card_data"
			:style="{ zIndex: 5 - index }"
			:data-id="index"
			:key="index"
			:animation="item.anim"
			@touchstart="touchStart"
			@touchmove="touchMove"
			@touchend="touchEnd"
		>
			<image class="card_item_image" :src="item.img" mode="aspectFill"></image>
			<!-- 喜欢按钮 -->
			<view class="card_item_type card_item_type_like" :style="{ display: item.like_state == -1 ? 'block' : 'none' }">
				<image src="../../static/SJ-CardPageTurning/like1.png" mode="aspectFill"></image>
			</view>
			<!-- 不喜欢按钮 -->
			<view class="card_item_type card_item_type_dislike" :style="{ display: item.like_state == 1 ? 'block' : 'none' }">
				<image src="../../static/SJ-CardPageTurning/dislike1.png" mode="aspectFill"></image>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	components: {},
	data() {
		return {
			startX: 0, //滑动开始x轴位置
			startY: 0, //滑动开始y轴位置
			moveX: 0, //滑动的x轴距离
			moveY: 0, //滑动的y轴距离
			like_state: 0, //-1：左滑，0：没滑动，1：右滑
			currentIndex: -1, //当前滑动的卡片index
			skewDeg: 0, //当前滑动卡片的倾斜度
			card_data: [
				{
					img: '../../static/SJ-CardPageTurning/card_img/card1.jpg',
					anim: null,
					like_state: 0
				},
				{
					img: '../../static/SJ-CardPageTurning/card_img/card2.jpg',
					anim: null,
					like_state: 0
				},
				{
					img: '../../static/SJ-CardPageTurning/card_img/card3.jpg',
					anim: null,
					like_state: 0
				},
				{
					img: '../../static/SJ-CardPageTurning/card_img/card4.jpg',
					anim: null,
					like_state: 0
				},
				{
					img: '../../static/SJ-CardPageTurning/card_img/card5.jpg',
					anim: null,
					like_state: 0
				}
			]
		};
	},
	onLoad() {},

	methods: {
		/**
		 * 触摸开始：记录位置
		 * */
		touchStart(event) {
			this.startX = event.touches[0].pageX;
			this.startY = event.touches[0].pageY;
		},
		/**
		 * 触摸开始滑动
		 * */
		touchMove(event) {
			var currentX = event.touches[0].pageX;
			var currentY = event.touches[0].pageY;
			var moveX = currentX - this.startX;
			var moveY = currentY - this.startY;
			var text = '';
			var currentIndex = event.currentTarget.dataset.id;
			var state = 0; //-1：左滑，0：没滑动，1：右滑
			// //左右方向滑动
			if (Math.abs(moveX) > Math.abs(moveY)) {
				if (moveX < -10) {
					text = '左滑';
					state = -1;
				} else if (moveX > 10) {
					text = '右滑';
					state = 1;
				}
				this.skew(currentIndex, moveX, moveY);
			} else {
				//上下方向滑动
				if (moveY < 0) text = '上滑';
				else if (moveY > 0) text = '下滑';
			}
			this.card_data[currentIndex]['text'] = text;
			this.card_data[currentIndex]['like_state'] = state;
			this.like_state = state;
			this.currentIndex = currentIndex;
			this.moveX = moveX;
			this.moveY = moveY;
		},
		/**
		 * 触摸结束
		 * */
		touchEnd(event) {
			// console.log(`移动距离:${Math.abs(this.moveX)}`)
			if (Math.abs(this.moveX) > 60) {
				this.hidden();
			} else {
				var anim = uni.createAnimation({
					duration: 300,
					timingFunction: 'ease-in-out'
				});
				anim.rotate(0).step(1000);
				this.card_data[this.currentIndex]['anim'] = anim.export();
				this.card_data[this.currentIndex]['like_state'] = 0;
			}
		},
		/**
		 * 触摸卡片倾斜
		 * */
		skew(index, moveX, moveY) {
			let that = this;
			var anim = uni.createAnimation({
				duration: 500,
				timingFunction: 'linear'
			});
			this.card_data[index]['anim'] = anim;
			if (Math.abs(moveX) < 180) {
				this.skewDeg;
				//console.log(`角度：${this.skewDeg}`)
				this.skewDeg = moveX / 4;
				anim.rotate(this.skewDeg).step(1000);
				this.card_data[index]['anim'] = anim.export();
			}
		},
		/**
		 * 触摸结束，卡片消失
		 * */
		hidden() {
			var anim = uni.createAnimation({
				duration: 400,
				timingFunction: 'ease-in-out'
			});
			if (this.like_state == -1) {
				anim.translate(-400, -400);
			} else if (this.like_state == 1) {
				anim.translate(400, -400);
			}
			// console.log(`角度：${this.skewDeg}`)
			anim.rotate(this.skewDeg)
				.opacity(0)
				.step(1000);
			this.card_data[this.currentIndex]['anim'] = anim.export();
		}
	}
};
</script>

<style lang="scss" scoped>
@import './SJ-CardPageTurning.scss';
</style>
