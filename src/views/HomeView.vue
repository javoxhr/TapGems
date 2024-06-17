<template>
  <main class="content">
    <div class="time-open">
      <h1>Совсем скоро</h1>
      <h1 class="gems">💎</h1>
    </div>

    <div class="limit">
      <span>
        <span></span>
      </span>
    </div>

    <div class="top">
      <div class="container">
        <div class="header-wrapper">
          <h1 class="header-wrapper__balance">{{ total }} G</h1>
          <h2 class="header-wrapper__text">Ваши монеты</h2>
        </div>
      </div>
    </div>

    <div class="coin-tap">
      <div class="container">
        <div class="coin-wrapper">
          <div class="coin-round">
            <button class="coin" @click="addTotal()">💎</button>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue';

const total = ref(10);

function addTotal() {
  total.value += 1; // Увеличение значения total на 1 при каждом клике
}
</script>

<style scoped>
.content {
  width: 100%;
  height: 100%;
  background-color: lightblue;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.top {
  margin-top: 20px;
}

.coin {
  font-size: 24px;
  padding: 10px;
  cursor: pointer;
}
</style>