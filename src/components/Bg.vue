<template>
	<div class="bg">
		<transition name="fade" mode="out-in">
			<img v-bind:src="imgurl" :key="imgurl" style="height:100%;width:100%" @click="movetoNext"/>
		</transition>
	</div>
</template>

<script>
	export default{
		name:'bg',
		props:['imgurl','stage'],
		data(){
			return{
				_imgurl:'../../common/images/1-1.jpg',
				_stage:"",
			}
		},
		methods:{
			movetoNext(){
				//location.href = this._tourl;
				this.$emit('toNext',this._stage);
			}
		},
		created(){
			//this._imgurl=this.imgurl;
			//console.log(this._imgurl)
			this._imgurl=this.imgurl;
			this._stage=this.stage;
		}


	}
</script>

<style scoped>
	.bg{
		position:fixed;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
		/* background: url("../../common/images/1-1.jpg") no-repeat;
		background-size: cover; */
		/* z-index: -1; */
	}
	.fade-enter {
		opacity:0.3;
	}
	.fade-leave{
		opacity:0.7;
	}
	.fade-enter-active{
		transition:opacity .3s;
	}
	.fade-leave-active{
		opacity:0;
		transition:opacity .3s;
	}
</style>