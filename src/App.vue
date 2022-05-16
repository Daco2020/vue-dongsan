<template>
  <div>
  
  <div class="black-bg" v-if="isShowModal">
    <div class="white-bg">
      <h4>상세</h4>
      <p>상세내용</p>
      <button @click="modalOff">창 닫기</button>
    </div>
  </div>
  
  <div class="menu">
    <a v-for="(v,i) in menus" :key="i">{{ v }}</a>
  </div>
  
  <div v-for="product, i in products" :key="i">
    <img :src="product.image" class="room-img">
    <h4 @click="modalOn">{{ product.title }}</h4>
    <p>{{ product.price }} 원</p>
    <button @click="increaseReport(i)">허위매물신고</button>
    <span> 신고수 : {{reportCount[i]}}</span>
  </div>
  </div>
</template>

<script>

import mockData from './assets/mockData.js';

export default {
  name: 'App',
  data(){
    return {
      isShowModal : false,
      reportCount : [0,0,0,0,0,0],
      menus : ["Home", "Product", "About"],
      locals : {역삼동원룸:50, 천호동원룸:60, 마포구원룸:70, 광진구원룸:80},
      products: mockData,
    }                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
  },
  methods : {
    increaseReport(i){
      this.reportCount[i]++
    },
    modalOn(){
      this.isShowModal = true
    },
    modalOff(){
      this.isShowModal = false
    }
  },
  components: {
  },
}
</script>

<style>
body {
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}



.room-img {
  width: 50%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: tomato;
  padding: 15px;
  border-radius:5px;

}
.menu a {
  color :white;
  padding : 10px;
}

</style>
