<template>
  <main class="content">
    <div class="overlay"></div>
    <div class="time-open">
      <h1>Совсем скоро</h1>
      <h1 class="gems">💎</h1>
    </div>

    <div class="limit">
      <span>
        <span></span>
      </span>
    </div>

    <top>
      <div class="container">
         <div class="header-wrapper">
            <h1 class="header-wrapper__balans">
              <span class="total">{{ total }}</span>
              <span class="zap">.</span>
              <span>{{ centerCoin }}</span>
              <span class="cash">{{ coin }}</span>
              G
            </h1>
            <h2 class="header-wrapper__text">Ваши монеты</h2>
         </div>
       </div>
    </top>

    <div class="coin-tap">
      <div class="container">
        <div class="coin-wrapper">
          <div class="coin-rount" @click="addTotal()">
            <button class="coin">💎</button>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
 import { ref } from 'vue';

 const total = ref(0)
 const coin = ref(0)
 const centerCoin = ref(0)
 
 function addTotal() {
  total.value += 1
  if(total.value >= 10) {
    total.value = 0
    centerCoin.value += 1
    if(centerCoin.value >= 10) {
      centerCoin.value = 0
      coin.value += 1
    }
  }
 }
</script>

<style lang="scss" scoped>
  .total {
    letter-spacing: 5px;
  }
  .zap {
    font-weight: 400;
    font-size: 30px;
    position: absolute;
    left: 27px;
    top: 20px;
  }
</style>