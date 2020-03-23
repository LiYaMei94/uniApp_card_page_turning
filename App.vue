<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	* {
	  margin: 0;
	  padding: 0;
	}
	a {
	  text-decoration: none !important;
	}
	li {
	  list-style: none;
	}
	html,
	body {
	  height: 100%;
	  /*点击出现的半透明背景*/
	  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
	  background-color: #F0F0F0;
	  /* background-color: #edf2f6; */
	}
	button {
	  outline: none;
	}
	:focus {
	  outline: 0;
	}
	input {
	  border: 0;
	  /*去除未选中状态边框*/
	  outline: none;
	  /*去除选中状态边框*/
	}
	.h1,
	.h2,
	.h3,
	.h4,
	.h5,
	.h6,
	h1,
	h2,
	h3,
	h4,
	h5,
	h6 {
	  margin-bottom: 0.5rem;
	  font-weight: 700;
	  line-height: 1.3;
	  color: #333132;
	}
	em, i, u{
		font-style: normal;
	}
</style>
