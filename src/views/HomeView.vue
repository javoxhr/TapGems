<template>
  <main>
    <div class="time-open">
      <h1>Совсем скоро</h1>
      <h1 class="gems">💎</h1>
    </div>

    <top>
      <div class="container">
         <div class="header-wrapper">
            <h1 class="header-wrapper__balans">{{ total }} G</h1>
            <h2 class="header-wrapper__text">Ваше монеты</h2>
         </div>
       </div>
    </top>

    <div class="coin-tap">
      <div class="container">
        <div class="coin-wrapper">
          <div class="coin-rount">
            <button class="coin">💎</button>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
let total = 0
</script>

<style>

</style>