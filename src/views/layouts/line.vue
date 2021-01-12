<template>
  <div class="app-container">
    <bg :imgurl='img'></bg>
    <div class="grid">
	<div class="item" @click="move"></div>
	<div class="item"></div>
	<div class="item"></div>
	<div class="item"></div>
	<div class="item"></div>
	<div class="item"></div>
    </div>
  </div>
</template>

<script>
import Bg from '@/components/Bg'
export default {
   name: 'Linet',
   data(){
       return{
           img:""
       }
   },
   components: {
    Bg
  },
  methods:{
      move(){
          this.$router.go(-1);
      }
  },
  mounted(){
      this.img=require('@/assets/images/background.jpg');
  }
}
</script>
<style scoped>
    .grid{
        display: grid;
		position:fixed;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
        padding-top:1rem;
        padding-bottom:1rem;
        padding-left:1rem;
        padding-right:1rem;
        grid-template-columns: 1fr 1fr;  /* 三列 */
        grid-template-rows: 1fr 1fr 1fr;
        grid-column-gap: 1rem;
        grid-row-gap:1rem;
        z-index:1;
    }
    .item:nth-child(1){background-image: url('~@/assets/images/drum.png');
                       background-size: cover;}
    .item:nth-child(2){background-image: url('~@/assets/images/textdrum1.png');
                       background-size: cover;}
    .item:nth-child(3){background-image: url('~@/assets/images/drum2.png');
                       background-size: cover;}
    .item:nth-child(4){background-image: url('~@/assets/images/textdrum2.png');
                       background-size: cover;}
    .item:nth-child(5){background-image: url('~@/assets/images/drum3.png');
                       background-size: cover;}
    .item:nth-child(6){background-image: url('~@/assets/images/textdrum31.png');
                       background-size: cover;}
</style>