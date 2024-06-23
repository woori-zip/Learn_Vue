<template>

  <div class="discount">
    <h4>지금 결제하면 20% 할인</h4>
  </div>

  <!-- Component -->
  <DiscountBanner></DiscountBanner>

  <!-- 모달창 -->
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>{{ 원룸들[누른거].title }}</h4>
      <img :src="원룸들[누른거].image" class="room-img">
      <p>가격: {{ 원룸들[누른거].price }}</p>
      <p>{{ 원룸들[누른거].content }}</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>

  <!-- <h1>* 반복문 *</h1>
  <div v-for="(a,i) in products" :key="i">
    <img :src="getRoomImg(i)" class="room-img">
    <h4 @click="모달창열렸니 = true">{{ a }}</h4>
    <p>50만 원</p>
    <button @click="신고수[i]++">허위매물신고</button> <span>신고수 : {{ 신고수[i] }}</span>
  </div>

  <hr>

  <h1>* 이벤트 핸들러 *</h1>
  <div>
    <img src="../assets/room0.jpg" class="room-img">
    <h4 @click="모달창열렸니 = true">{{ products[0] }}</h4>
    <p>{{ prices[0] }}</p>
    <button @click="신고수[0]++">허위매물신고</button> <span>신고수 : {{ 신고수[0] }}</span>
  </div>
  <div>
    <img src="../assets/room1.jpg" class="room-img">
    <h4 @click="모달창열렸니 = true">{{ products[1] }}</h4>
    <p>{{ prices[1] }}</p>
    <button @click="신고수[1]++">허위매물신고</button> <span>신고수 : {{ 신고수[1] }}</span>
  </div>
  <div>
    <img src="../assets/room2.jpg" class="room-img">
    <h4 @click="모달창열렸니 = true">{{ products[2] }}</h4>
    <p>{{ prices[2] }}만 원</p>
    <button @click="신고수[2]++">허위매물신고</button> <span>신고수 : {{ 신고수[2] }}</span>
  </div>

  <hr>

  <h1>* json 에서 데이터 불러오기 *</h1>
  <div>
    <img :src="원룸들[0].image" class="room-img">
    <h4>{{ 원룸들[0].title }}</h4>
    <p>{{ 원룸들[0].price }}</p>
  </div>
  <div>
    <img :src="원룸들[1].image" class="room-img">
    <h4>{{ 원룸들[1].title }}</h4>
    <p>{{ 원룸들[1].price }}</p>
  </div>
  <div>
    <img :src="원룸들[2].image" class="room-img">
    <h4>{{ 원룸들[2].title }}</h4>
    <p>{{ 원룸들[2].price }}</p>
  </div>
  <div>
    <img :src="원룸들[3].image" class="room-img">
    <h4>{{ 원룸들[3].title }}</h4>
    <p>{{ 원룸들[3].price }}</p>
  </div>

  <hr> -->

  <h1>* json 에서 데이터 불러오기(반복문) *</h1>
  <div v-for="(작명,i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" class="room-img">
    <h4 @click="모달창열렸니 = true; 누른거 = i">{{ 원룸들[i].title }}</h4>
    <p>가격: {{ 원룸들[i].price }}</p>
  </div>

  <div v-if="1 == 2">
    안녕하세요1
  </div>
  <div v-else>
    안녕하세요2
  </div>

  <hr>
</template>

<script>
import data from '../assets/data'
import DiscountBanner from '../DiscountBanner.vue'

export default {
  name: 'App',
  data () {
    return {
      누른거: 0,
      모달창열렸니: false,
      신고수: [0, 0, 0],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      prices: ['50', '60', '100'],
      원룸들: data
    }
  },
  methods: {
    increase (i) {
      this.신고수[i]++
    },
    getRoomImg (i) {
      return require('../assets/room' + i + '.jpg')
    }
  },
  components: {
    DiscountBanner: DiscountBanner
  }
}
</script>

<style>
body{
  margin:0
}
div{
  box-sizing: border-box;
}
.black-bg{
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgb(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%;  background: white;
  border-radius: 8px; padding:20px;
}
.room-img{
  width: 300px;
}
.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
