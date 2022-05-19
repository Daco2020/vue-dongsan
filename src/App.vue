<template>
  <div>

  <modal :products="products" :currentProduct="currentProduct" :isShowModal="isShowModal" :modalOff="modalOff"/>

  <div class="menu">
    <a v-for="(v,i) in menus" :key="i">{{ v }}</a>
  </div>

  <discount/>
  
  <div v-for="product, i in products" :key="i">
    <img :src="product.image" class="room-img">
    <h4 @click="modalOn(), currentProduct = i" >{{ product.title }}</h4>
    <p>{{ product.price }} 원</p>
    <button @click="increaseReport(i)">허위매물신고</button>
    <span> 신고수 : {{reportCount[i]}}</span>
  </div>



  </div>
</template>

<script>

import mockData from './assets/mockData.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';

export default {
  name: 'App',
  data(){
    return {
      isShowModal : false,
      reportCount : [0,0,0,0,0,0],
      menus : ["Home", "Product", "About"],
      products: mockData,
      currentProduct : 0,
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
    discount : Discount,
    modal : Modal,
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
  background: seagreen;
  padding: 15px;
  border-radius:5px;

}
.menu a {
  color :white;
  padding : 10px;
}

</style>
