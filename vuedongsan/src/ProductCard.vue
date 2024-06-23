<template>
<h1>* json 에서 데이터 불러오기(반복문) *</h1>
<div v-for="(작명,i) in 원룸들" :key="i">
  <img :src="원룸들[i].image" class="room-img">
  <h4 @click="모달창열렸니 = true; 누른거 = i">{{ 원룸들[i].title }}</h4>
  <p>가격: {{ 원룸들[i].price }}</p>
</div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    원룸들: Array,
    모달창열렸니: Boolean
  }
}
</script>

<style>

</style>
