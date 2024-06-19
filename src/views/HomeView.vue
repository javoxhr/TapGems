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
              <span :style="{'display': total >= 1000 ? 'none' : 'block'}">0</span>
              <span class="zap">,</span>
              <span :style="{'display': total >= 100 ? 'none' : 'block'}">0</span>
              <span :style="{'display': total >= 10 ? 'none': 'block'}">0</span> 
              <span class="total">{{ total }}</span> G</h1>
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
 
 function addTotal() {
  total.value += 1
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
    left: 22px;
    top: 20px;
  }
</style>