<template>
  <div class="app-container">
    <bg v-bind:imgurl='img' v-bind:stage='sta' @toNext="move"></bg>
    <img :src='text1' v-if="text1on" style="z-index:100;width:100%;" @click= "move">
    <!-- <div class="layout-content">
      <keep-alive v-if="$route.meta.keepAlive">
        <router-view></router-view>
      </keep-alive>
      <router-view v-else></router-view>
    </div>
    <div class="layout-footer">
      <TabBar :data="tabbars" @change="handleChange" />
    </div> -->
  </div>
</template>

<script>
import TabBar from '@/components/TabBar'
import Bg from '@/components/Bg'
export default {
  name: 'AppLayout',
  data() {
    return {
      img:'../../common/images/1-1.jpg',
      sta:"1-1",
      text1:"",
      text1on:false,
      top:7
    }
  },
  components: {
    Bg
  },
  methods: {
    handleChange(v) {
      console.log('tab value:', v)
    },
    move(){
      //console.log("moved",stage);
      if (this.sta=="1-1"){
        this.img=require("@/assets/images/battlefield.jpg");
        this.sta="2-1";
        this.text1on=true;
      }
      else if (this.sta=="2-1"){
        this.text1on=false;
        this.img=require("@/assets/images/3-1.jpg");
        this.sta="2-2";
      }
      else if (this.sta=="2-2"){
        this.img=require("@/assets/images/3-2.jpg");
        this.sta="2-3";
      }
      else if (this.sta=="2-3"){
        this.img=require("@/assets/images/4-1.jpg");
        this.sta="2-4"
      }
      
    }
  },
  created(){
      this.img=require("@/assets/images/1-1.jpg");
      this.text1=require("@/assets/images/text1.png")
  },
}
</script>
