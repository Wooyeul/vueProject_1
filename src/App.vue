
<template>

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>{{상세내용}}</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a">{{a}}</a>
  </div>

  <div v-for="(a, i) in 원룸들" :key="i">
    <img :src="a.image" class="room-img"/>
    <h4>{{a.title}}</h4>
    <p>{{a.price}}원</p>
    <button @click="openModal(i)">상세보기</button>
  </div>
</template>

<script>

  import data from './oneroom.js';

  export default {
    name: 'App',
    data(){
      return {
        상세내용: '',
        원룸들 :data,
        모달창열렸니 : false,
        신고수 : [0, 0, 0],
        메뉴들 : ['Home', 'Shop', 'About'],
        products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      }
    },
    methods: {
      increase(i){
        this.신고수[i] += 1;
      },
      openModal(i) {
        this.모달창열렸니 = true;
        this.상세내용 = this.원룸들[i].content;
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

  .room-img {
    width: 100%;
    margin-top: 40px;
  }

  body {
    margin : 0;
  }

  div {
    box-sizing: border-box;
  }

  .black-bg {
    width: 100%; height:100%;
    background: rgba(0,0,0,0.5);
    position: fixed; padding: 20px;
  }

  .white-bg {
    width: 100%; background: white;
    border-radius: 8px;
    padding: 20px;
  } 
</style>
