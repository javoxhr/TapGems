<template>
  <main class="content">
    <div class="overlay"></div>
    <div class="time-open">
      <h1>Совсем скоро</h1>
      <h1 class="gems">💎</h1>
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
          <div class="coin-rount" @click="addTotal(), calc -= 5">
            <button class="coin"><img class="rubiy" src="../assets/images/599608.png" alt=""></button>
          </div>
        </div>
      </div>
    </div>

    <div class="limit">
      <span>
        <span :style="{'width': calc + 'px'}"></span>
      </span>
    </div>
  </main>
</template>

<script setup>
 import { ref } from 'vue';

 const total = ref(0)
 const coin = ref(0)
 const centerCoin = ref(0)

 const calc = ref(300)

function intervalFunc() {
  setInterval(()=> {
  if(calc.value == 300) {
    calc.value = 300
  } else {
    calc.value += 2
  }
 }, 1000)
}

intervalFunc()

 
 function addTotal() {
  if(calc.value >= 0) {
    total.value += 1
  } else {
    total.value += 0
    intervalFunc()
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
    margin-top: 12px;
  }

  .rubiy {
    display: flex;
    width: 180px;
  }
</style>