<template>
  <div class="overlay"></div>
  <div class="loader" :style="{'display': show == true ? 'none' : 'none'}">
    <span class="loading"></span>
    <span class="loading"></span>
    <span class="loading"></span>
    <span class="loading"></span>
  </div>
  <main class="content">
    <div class="time-open">
      <h1>Совсем скоро</h1>
      <h1 class="gems">💎</h1>
    </div>

    <top>
      <div class="container">
        <div class="header-wrapper">
          <h1 class="header-wrapper__balans" :class="{'after-balans': show == true}"  >
            <span class="total">{{ total }}</span>
            <span class="zap">.</span>
            <span>{{ centerCoin }}</span>
            <span class="cash">{{ coin }}</span>
            G
          </h1>
        </div>
      </div>
    </top>

    <div class="coin-tap">
      <div class="container">
        <div class="coin-wrapper">
          <div class="coin-rount" @click="addTotal(), showFunc(), vibrate(), (calc -= 5)">
            <button class="coin">
              <img class="rubiy" src="../assets/images/rubiy-coin.png" alt="">
            </button>
          </div>
        </div>
      </div>
    </div>

    <div class="limit">
      <div class="limit-wrap">
        <button class="energiya">
          <img src="../assets/images/energiy.svg" alt="" />
        </button>
        <h1 class="limit-text">{{ calc }}</h1>
        <h3 class="slash">/</h3>
        <h1 class="limit-text">300</h1>
      </div>
      <span>
        <span :style="{ width: calc + 'px' }"></span>
      </span>
    </div>
  </main>
</template>

<script setup>
import { ref, onMounted } from "vue";

const total = ref(0);
const coin = ref(0);
const centerCoin = ref(0);

const calc = ref(300);

let show = ref(false)


function showFunc() {
  show.value = !show.value
}

function vibrate() {
  if("vibrate" in navigator) {
    navigator.vibrate([100, 50, 100, 50, 100])
  } else {
    console.log('Вибрация не поддерживается этим устройством.')
  }
}

function addTotal() {
  if (calc.value >= 0) {
    total.value += 1;
  } else {
    console.log("hello");
    total.value += 0;
  }
  localStorage.setItem("count", total.value);
}
onMounted(() => {
  total.value = localStorage.getItem("count")
    ? Number(localStorage.getItem("count"))
    : 0;
  setInterval(() => {
    if (calc.value !== 300 || calc.value < 300) {
       calc.value += 5;
    }
  }, 1500);
});
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
.limit-text {
  font-weight: 400;
  font-size: 16px;
}
.slash {
  font-weight: 400;
  font-size: 18px;
  padding: 0 3px;
}
</style>