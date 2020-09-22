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
    <Fire :x="0" :y="437" />
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
import Fire from './Fire.vue';

export default defineComponent({
  name: 'SecondStage',
  emits: ['deployed'],
  components: {
    Fire,
  },
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

  & .fire {
    visibility: hidden;
  }
}

g.launched .stage-2 {
  animation-name: ride-first-stage, second-stage-burn, orbit, de-orbit;
  animation-duration: 1s, 2s, 6s, 3s;
  animation-timing-function: linear, linear, linear, linear;
  animation-fill-mode: forwards;
  animation-iteration-count: 1, 1, 2.4, 1;
  animation-delay: 0s, 1s, 3s, 12s;

  & .fire {
    animation-name: ignition, ignition, ignition;
    animation-duration: 2.5s, 0.8s, 1s;
    animation-timing-function: linear;
    animation-fill-mode: forwards;
    animation-delay: 1.2s, 12.8s, 14s;
    animation-direction: normal;
  }
}

g.launched .fairing {
  animation-duration: 2s, 2s;
  animation-timing-function: linear, linear;
  animation-fill-mode: forwards, forwards;
  animation-delay: 6s, 9s;
  animation-direction: normal, reverse;
}

g.launched .left {
  animation-name: open-left-fairing, open-left-fairing;
}

g.launched .right {
  animation-name: open-right-fairing, open-right-fairing;
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
    transform: rotate(0deg) translateX(151px) scale(0.08) rotateZ(180deg);
  }
  to {
    transform: rotate(360deg) translateX(151px) scale(0.08) rotateZ(180deg);
  }
}

@keyframes de-orbit {
  40% {
    transform: rotate(200deg) translateX(151px) scale(0.08) rotateZ(52deg);
  }
  60% {
    transform: rotate(220deg) translateX(131px) scale(0.08) rotateZ(0deg);
  }
  60% {
    transform: rotate(240deg) translateX(111px) scale(0.08) rotateZ(0deg);
  }
  90% {
    transform: translate(-36px, -85px) scale(0.08);
  }
  100% {
    transform: translate(-36px, -50px) scale(0.08);
  }
}

@keyframes open-left-fairing {
  0% {
    transform: translate(0px, 0px);
  }
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
  0% {
    transform: rotate(90deg) translate(27px, -165px);
  }
  50% {
    /* Slide out */
    transform: rotate(90deg) translate(27px, -202px);
  }
  100% {
    /** Slide down */
    transform: rotate(90deg) translate(139px, -202px);
  }
}

@keyframes ignition {
  0% {
    visibility: hidden;
  }
  1% {
    visibility: visible;
  }
  100% {
    visibility: hidden;
  }
}
</style>
