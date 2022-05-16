<template>
  <div>
  <div class="menu">
    <a v-for="(v,i) in menus" :key="i">{{ v }}</a>
  </div>
  <div v-for="(v,k,i) in locals" :key="i">
    <h4 :style=style>{{ k }}</h4>
    <p>{{ v }} 만원</p>
    <button @click="increaseReport(i)">허위매물신고</button> <span>신고수 : {{reportCount[i]}}</span>
  </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      reportCount : [0,0,0,0],
      menus : ["Home", "Product", "About"],
      locals : {역삼동원룸:50, 천호동원룸:60, 마포구원룸:70, 광진구원룸:80}
    }                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
  },
  methods : {
    increaseReport(i){
      this.reportCount[i]++
    }
  },
  components: {
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
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
