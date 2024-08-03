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
          <div class="coin-rount" @click="clickFunc">
            <audio ref="audioElement">
              <source src="/IMG_5651.mp3" type="audio/mpeg">
            </audio>
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
          <!-- <img src="../assets/images/energiy.svg" alt="" /> -->
         <!DOCTYPE svg  PUBLIC '-//W3C//DTD SVG 1.1//EN'  'http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd'>
         <svg enable-background="new 0 0 512 512" height="512px" id="Слой_1" version="1.1" viewBox="0 0 512 512" width="512px" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><g><g><g><path clip-rule="evenodd" d="M336.949,83.675c0.35,0.002,0.697,0.002,1.048,0h1.048    
            c0.455,0.011,0.9,0.029,1.339,0.059c7.456,0.473,13.878,3.421,19.262,8.844c5.953,5.948,8.94,13.125,8.963,21.53v332.837    
              c-0.005,0.471-0.025,0.937-0.059,1.396c-0.321,7.806-3.287,14.518-8.904,20.134c-5.577,5.644-12.249,8.633-20.019,8.96    
              c-0.443,0.036-0.889,0.055-1.339,0.06H173.654c-0.412-0.005-0.818-0.023-1.222-0.06c-7.817-0.315-14.528-3.303-20.136-8.96     
              c-5.936-5.946-8.903-13.124-8.904-21.529V114.108c0.001-8.405,2.969-15.582,8.904-21.53c5.889-5.935,13.008-8.901,21.357-8.903    
              v0.059c86.639-0.03,140.374-0.05,161.201-0.059C335.554,83.68,336.251,83.68,336.949,83.675z M225.972,408.018v20.714h60.116  
             v-20.714H225.972z M206.011,297.808h39.514l-17.982,62.262c-0.359,1.248-0.282,2.471,0.233,3.667     
              c0.512,1.186,1.346,2.079,2.503,2.677c1.149,0.609,2.352,0.784,3.607,0.523c1.27-0.269,2.317-0.909,3.143-1.921l73.267-91.472   
             c0.869-1.116,1.237-2.378,1.107-3.782c-0.091-1.423-0.652-2.625-1.689-3.607c-1.057-0.993-2.298-1.498-3.724-1.514h-39.513     
             l17.981-62.202c0.358-1.289,0.281-2.548-0.232-3.782c-0.514-1.168-1.346-2.041-2.503-2.618    
            c-1.171-0.594-2.394-0.748-3.667-0.467c-1.291,0.269-2.356,0.909-3.2,1.921l-73.15,91.472c-0.907,1.096-1.315,2.337-1.224,3.724  
            c0.129,1.44,0.73,2.663,1.806,3.666C203.343,297.326,204.585,297.811,206.011,297.808z M266.358,132.496V112.77H245.7v19.727  
            h-19.729v20.714H245.7v19.728h20.658V153.21h19.729v-20.714H266.358z"
             :fill="svgColor" fill-rule="evenodd"/></g><g><rect clip-rule="#fff"
           :fill="svgColor" fill-rule="evenodd" height="32px" width="106px"
            x="202.984" y="33.808"/></g></g></g></svg>
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
const audioElement = ref(null);

const playAudio = () => {
  const audio = new Audio('/IMG_5651.mp3');
  audio.play().catch(error => {
    console.error("Ошибка воспроизведения звука:", error);
  });
};

const total = ref(0);
const coin = ref(0);
const centerCoin = ref(0);

const calc = ref(300);
const show = ref(false);
const svgColor = ref('#9acd32');

const clickFunc = () => {
  addTotal();
  showFunc();
  vibrate();
};

const showFunc = () => {
  show.value = !show.value;
};

const vibrate = () => {
  if (navigator.vibrate) {
    navigator.vibrate(200);
    console.log('hello world');
  } else {
    console.log('Вибрация не поддерживается этим устройством.');
  }
};

const addTotal = () => {
  if (calc.value <= 50) {
    svgColor.value = 'Brown';
  } else {
    svgColor.value = '#9acd32';
  }
  
  if (calc.value >= 5) {
    total.value += 1;
    calc.value -= 5;
    playAudio();
  } else {
    console.log("hello");
  }
  
  localStorage.setItem("count", total.value);
};

onMounted(() => {
  total.value = localStorage.getItem("count") ? Number(localStorage.getItem("count")) : 0;
  
  setInterval(() => {
    if (calc.value < 300) {
      calc.value += 5;
    }
  }, 3000);
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

.energiya {
  svg {
    width: 20px;
    height: 20px;
  }
}
</style>