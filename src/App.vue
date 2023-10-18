<template>
  <p text-align="center">{{ logo }}</p>

  <div class="menu">
    <a v-for="(item, i) in menus" :key="item">{{ i }}.{{ item }}</a>
  </div>

  <div v-for="(p, j) in products" :key="j">
    <img src="{{ imgs[j] }}">
    <h4 :style="스타일[j]">{{ p }}</h4>
    <p>{{ prices[j] }} 만원</p>
    <button @click="신고수[j]++" @mouseover="countplus(j)">허위매물신고</button> <span>신고수 : {{ 신고수[j] }}</span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){ //data 보관함
    return {  
        logo : '원룸샵',
        menus : ['Home','Products','About'],
        imgs : ['./assets/room0.jpg', './assets/room1.jpg', './assets/room2.jpg'],
        스타일 : ['color : black','color : lightblue','color : green'],
        products : ['역삼동 원룸','천호동 원룸','마포구 원룸'],
        prices : [80,70,100],
        신고수 : [0, 0, 0],
    }
  },
  methods : {
    countplus (j){
      this.신고수[j] += 1;
    }
  },
  components: {

  }
}
</script>

<style>
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
</style>
