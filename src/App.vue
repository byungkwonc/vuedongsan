<template>

  <p text-align="center">{{ logo }}</p>

  <div class="black-bg" v-if="modalopenstatus == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="closemodal()">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(item, i) in menus" :key="item">{{ i }}.{{ item }}</a>
  </div>

<!--   <div v-for="(p, j) in products" :key="j">
    <img :src="require(`@/assets/room${j}.jpg`)" class="room-img">
    <h4 :style="스타일[j]" @click="openmodal">{{ p }}</h4>
    <p>{{ prices[j] }} 만원</p>
    <button @click="신고수[j]++" @mouseover="countplus(j)">허위매물신고</button> <span>신고수 : {{ 신고수[j] }}</span>
  </div> -->

  <div v-for="(p, j) in onerooms" :key="j">
    <img :src="`${onerooms[j].image}`" class="room-img">
    <h4 @click="openmodal">{{ onerooms[j].title }}</h4>
    <p>{{ onerooms[j].price }}원</p>
  </div>

</template>

<script>
import oneroomdata from './components/oneroom.js';

export default {
  name: 'App',
  data(){ //data 보관함
    return {  
        logo : '원룸샵',
        menus : ['Home','Products','About'],
        // 스타일 : ['color : black','color : lightblue','color : green'],
        // products : ['역삼동 원룸','천호동 원룸','마포구 원룸'],
        // prices : [80,70,100],
        // 신고수 : [0, 0, 0],
        modalopenstatus : false,
        onerooms : oneroomdata,
    }
  },
  methods : {
    countplus (j){
      this.신고수[j] += 1;
    },
    openmodal (){
      this.modalopenstatus = true;
    },
    closemodal (){
      this.modalopenstatus = false; 
    }
  },
  components: {

  }
}
</script>

<style>
body {
  margin : 0
}
div {
  box-sizing : border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;  
}
</style>
