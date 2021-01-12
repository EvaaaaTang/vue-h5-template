<template>
  <div class="app-container">
    <bg v-bind:imgurl='img' v-show="bgon" v-bind:stage='sta' @toNext="move"></bg>
    <img :src='text1' v-if="text1on" style="z-index:100;width:100%;" @click= "move">
    <video class="vi" v-if="videoon" id="myvideo" :src="videoSrc" :autoplay="autoplay">
    </video>
     <div class="player">
    <div
      class="player-cd"
      id="trigger"
    >
    <audio id="audio" :src="audiosrc" loop></audio>
    </div>
     </div>
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
      videoon:false,
      videoSrc:"",
      top:7,
      autoplay: true,
      state: false,
      bgon:true,
      audiosrc:"",
    }
  },
  components: {
    Bg
  },
  methods: {
    handleChange(v) {
      console.log('tab value:', v)
    },
    createTouchstartEventAndDispatch (el) {
      let event = document.createEvent('Events');
      event.initEvent('touchstart', true, true);
      el.dispatchEvent(event);
    },
    move(){
      console.log("moved",this.sta);
      if (this.sta=="1-1"){
        this.sta="2-0";
        this.videoon=true;
        this.bgon=false;
        var self = this;
        this.$nextTick(() => {
          console.log("getting element");
          document.getElementById('myvideo').loop = false // 不设置视频循环播放  
          document.getElementById('myvideo').addEventListener('ended',function(){
            console.log("ended video playing")
            self.videoon=false;
            self.move();
          });
        });
      }
      else if (this.sta=="2-0"){
        this.bgon=true;
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
      else if (this.sta=="2-4"){
        this.img=require("@/assets/images/4-2.jpg");
        this.sta="2-5"
      }
      else if (this.sta=="2-5"){
        this.img=require("@/assets/images/4-3.jpg");
        this.sta="2-6"
      }
      else if (this.sta=="2-6"){
        this.img=require("@/assets/images/5-1.jpg");
        this.sta="2-7"
      }
      else if (this.sta=="2-7"){
        this.img=require("@/assets/images/5-2.jpg");
        this.sta="2-8"
      }
      else if (this.sta=="2-8"){
        this.img=require("@/assets/images/5-3.jpg");
        this.sta="2-9"
      }
      else if (this.sta=="2-9"){
        this.img=require("@/assets/images/5-4.jpg");
        this.sta="2-10";
        this.$router.push('/line')
      }
      
    }
  },
  created(){
      this.img=require("@/assets/images/1-1.jpg");
      this.text1=require("@/assets/images/text1.png");
      this.videoSrc=require("@/assets/videos/begin.mp4")
      this.audiosrc=require("@/assets/audio/opening.wav")
  },
  mounted () {  
      // document.getElementById('myvideo').loop = false // 不设置视频循环播放  
      // document.getElementById('myvideo').addEventListener('ended',function(){
      //           console.log("ended video playing")
      //           move();
      // });
      let trigger = document.getElementById('trigger')
      let audio = document.getElementById('audio')
      trigger.addEventListener('touchstart', () => {
        audio.play()
      })

      // 模拟触发 「touchstart」 事件
      this.createTouchstartEventAndDispatch(trigger)
  }
}
</script>

<style scoped>
	.vi{
		position:fixed;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
    width: 100%;
    height: 100%;
		/* background: url("../../common/images/1-1.jpg") no-repeat;
		background-size: cover; */
	}
</style>