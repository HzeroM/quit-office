<template>
  <div id="wrapper">
    <main>
      <div>
        <p class="height:100px">老子不干了！！！辞职</p>
        <div style="margin-top:20px;">
           <button @click="isYou" class="button">准了</button>
           <button class="button button2" :style="{top:top+'px',left:left+'px'}" @mouseenter="hover">不准</button>
        </div> 
      </div>
      <div v-if="show" class="alert">
        <div class="card">
            <p>再见臭傻逼！<img class="img" src="../assets/xiao.jpg"></p>
            <button @click="close" class="button">关闭</button>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import { remote } from 'electron';
  export default {
    name: 'landing-page',
    data(){
      return{
         top:100,
         left:200,
         show:false,
       
      }
    },
    methods: {
      hover(){
          
           this.top =Math.random()*220;
           this.left = Math.random()*400;
      },
      isYou(){
        this.show = true;
      },
      close(){
       this.$electron.ipcRenderer.send("window-close");
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body { font-family: 'Source Sans Pro', sans-serif; }

  #wrapper {
    background:
      radial-gradient(
        ellipse at top left,
        rgba(255, 255, 255, 1) 40%,
        rgba(229, 229, 229, .9) 100%
      );
    height: 100vh;
    padding: 60px 80px;
    width: 100vw;
  }

  main {
    display: flex;
    justify-content: space-between;
  }

  main > div { flex-basis: 50%; }
  .button{
    width:80px;
    height:40px;
  }
  .button2{
    position: absolute;
  }
 .alert{
   position: fixed;
   top:0;
   left:0;
   bottom:0;
   right:0;
   background-color: rgba(0, 0, 0, .4);
   display: flex;
  justify-content: center;
  align-items: center;
 }
 .img{
   width:100px;
   height:100px;
 }
 .card{
   text-align: center;
   width:300px;
   height:200px;
   background-color: #fff;
 }
</style>
