<template>
  <main class="content" :class="{ zoomed: isZoomed }">
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
          <div class="coin-round" @click="addTotal()">
            <button class="coin">💎</button>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
import { ref } from 'vue';

const total = ref(10);
const isZoomed = ref(false);

function addTotal() {
  total.value += 1;
}

const disableZoom = (e) => {
  e.preventDefault();
};

// Добавляем обработчики событий для предотвращения масштабирования
document.addEventListener('gesturestart', disableZoom);
document.addEventListener('gesturechange', disableZoom);
document.addEventListener('gestureend', disableZoom);
</script>

<style scoped>

</style>