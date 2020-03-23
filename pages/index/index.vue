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
	/* padding-top: 100upx;
	box-sizing: border-box; */
}

</style>
