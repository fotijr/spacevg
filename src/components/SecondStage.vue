<template>
  <g class="stage-2">
    <rect
      height="196"
      width="87.00001"
      y="248.5"
      x="4.5"
      stroke-width="1.5"
      stroke="#000"
      fill="#fff"
    />
    <path
      class="bell"
      d="m51.5725,463.81247l7.5,-19l25.00001,0l7.5,19l-40.00001,0z"
    />
    <path
      class="bell"
      d="m6.5725,463.81247l7.5,-19l25.00001,0l7.5,19l-40.00001,0z"
      fill-opacity="null"
      stroke-opacity="null"
    />
    <path
      class="fairing right"
      d="m-24.70498,81.16808l37.13758,-8.58557l148.8624,0l0,42.99999l-185.99999,0l0,-34.41443z"
      fill-opacity="null"
      stroke-opacity="null"
      stroke-width="1.5"
      stroke="#000"
      fill="#fff"
    />
    <path
      class="fairing left"
      d="m4.795,38.22012l8.18624,-37.13758l32.81375,0l0,185.99998l-40.99998,0l0,-148.8624z"
      fill-opacity="null"
      stroke-opacity="null"
      stroke-width="1.5"
      stroke="#000"
      fill="#fff"
    />
    <rect
      class="spacecraft-body"
      height="61"
      width="87"
      y="186.5"
      x="4"
      stroke-width="1.5"
      stroke="#000"
    />
  </g>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'SecondStage',
  emits: ['deployed'],
  setup() {
    const state = ref({
      launched: false,
      orbit: false,
    });
    const launch = () => {
      state.value.launched = true;

      setTimeout(() => {
        // state.value.orbit = true;
        this.$emit('deployed');
      }, 3000);
    };

    return {
      launch,
      state,
    };
  },
});
</script>

<style>
g.stage-2 {
  transform: translate(-36px, -85px) scale(0.08);
}

g.launched .stage-2 {
  animation-name: ride-first-stage, second-stage-burn, orbit;
  animation-duration: 1s, 2s, 6s;
  animation-timing-function: linear, linear, linear;
  animation-fill-mode: forwards;
  animation-delay: 0s, 1s, 3s;
}

g.launched .left {
  animation-name: open-left-fairing;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-fill-mode: forwards;
  animation-delay: 6s;
}

g.launched .right {
  animation-name: open-right-fairing;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-fill-mode: forwards;
  animation-delay: 6s;
}

.fairing.right {
  transform: rotate(90deg) translate(27px, -165px);
}

.spacecraft-body {
  stroke: #000;
  fill: #555;
}

@keyframes ride-first-stage {
  40% {
    /* max q */
    transform: translate(7px, -105px) scale(0.08) rotate(30deg);
  }
  100% {
    /* MECO */
    transform: translate(40px, -124px) scale(0.08) rotate(65deg);
  }
}

@keyframes second-stage-burn {
  20% {
    /* burn to orbit */
    transform: translate(70px, -123px) scale(0.08) rotate(75deg);
  }
  40% {
    transform: translate(110px, -101px) scale(0.08) rotate(117deg);
  }
  100% {
    transform: translate(151px, -49px) scale(0.08) rotate(172deg);
  }
}

@keyframes orbit {
  from {
    transform: rotate(0deg) translateX(151px) scale(0.08) scaleY(-1);
  }
  to {
    transform: rotate(360deg) translateX(151px) scale(0.08) scaleY(-1);
  }
}

@keyframes open-left-fairing {
  50% {
    /* Slide out */
    transform: translate(-46px, 25px);
  }
  100% {
    /** Slide down */
    transform: translate(-46px, 115px);
  }
}

@keyframes open-right-fairing {
  50% {
    /* Slide out */
    transform: rotate(90deg) translate(27px, -202px);
  }
  100% {
    /** Slide down */
    transform: rotate(90deg) translate(139px, -202px);
  }
}
</style>
