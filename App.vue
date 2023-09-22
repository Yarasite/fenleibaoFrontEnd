<script>
export default {
	onLaunch: function() {
		console.log('App Launch');

	},
	onShow: function() {
		console.log('App Show');
	},
	onHide: function() {
		console.log('App Hide');
	}
};
</script>

<style>
/*每个页面公共css */ 
	 page {
		 /* rgba会导致透明度叠加 */
	    /* background-color: rgba(204,247,83,0.5); */
		background-color: #e5fbc1;
		/* opacity: .5; */
	  }
  
</style>