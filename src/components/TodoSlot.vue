<template>
  <div>
    <token-counter :number="tokenNumber"></token-counter>
    <div>
      <transition name="rolling">
        <span>{{randomNum1}}</span>
      </transition>
      <span>{{randomNum2}}</span>
      <span>{{randomNum3}}</span>
    </div>

    <button @click="doRandom">slot！</button>
  </div>
</template>

<script>
import TokenCounter from './tokenCounter.vue'
export default {
  components: {
    'token-counter': TokenCounter,
  },
  data() {
    return {
      tokenNumber: 0,
      randomNum1: 0,
      randomNum2: 0,
      randomNum3: 0,
    }
  },
  methods: {
    doRandom() {
      this.randomNum1 = Math.round(Math.random() * 4);
      if (this.randomNum1 < 3) {
        this.randomNum2 = Math.round(Math.random() * 1 + 1);
      } else {
        this.randomNum2 = Math.round(Math.random() * 1 + 3);
      };
      if (this.randomNum2 < 3) {
        this.randomNum3 = Math.round(Math.random() * 1 + 1);
      } else {
        this.randomNum3 = Math.round(Math.random() * 1 + 3);
      };
      this.tokenNumber = this.tokenNumber - 1;
    }
  }

}
</script>


<style>
.rolling-fade-enter-active {
  transition: all .3s ease;
}

.rolling-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}

.rolling-fade-enter,
.rolling-fade-leave-to {
  transform: translateX(10px);
  opacity: 0;
}
</style>
