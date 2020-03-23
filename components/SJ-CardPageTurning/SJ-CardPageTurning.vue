<template>
	<div class="container"></div>
</template>

<script>
export default {
	data() {
		return {
		};
	},
	props: {
		grid_info_arr: {
			type: Array,
			default: function() {
				return [];
			}
		},
		lottery_draw_param: {
			type: Object,
			default: function() {
				return {
					startIndex: 0, //开始抽奖位置，从0开始
					totalCount: 4, //一共要转的圈数
					winingIndex: 2, //中奖的位置，从0开始
					speed: 50 //抽奖动画的速度 [数字越大越慢,默认100]
				};
			}
		}
	},
	onLoad() {},

	methods: {}
};
</script>

<style scoped lang="scss">
@import './SJ-CardPageTurning.scss';
</style>
