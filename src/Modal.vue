<template>
    <div class="black-bg" v-if="isShowModal">
    <div class="white-bg">
      <img :src="products[currentProduct].image" class="room-img">
      <h4>{{products[currentProduct].title}}</h4>
      <p>{{products[currentProduct].content}}</p>
      <p>{{products[currentProduct].price}} 원</p>
      <button @click="modalOff">창 닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name: "ModalComponent",
    props: {
        products: Array,
        currentProduct: Number,
        modalOff: Function,
        isShowModal: Boolean,
    }

}
</script>

<style>
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

</style>