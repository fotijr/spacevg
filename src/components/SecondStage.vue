<template>
  <g class="stage-2">
    <rect
      class="tank"
      height="196"
      width="87"
      y="248.5"
      x="4.5"
      stroke-width="1.5"
    />
    <Fire :x="0" :y="437" />
    <path class="bell" d="m51.5725,463.8l7.5,-19l25,0l7.5,19l-40,0z" />
    <path class="bell" d="m6.5725,463.8l7.5,-19l25,0l7.5,19l-40,0z" />
    <path
      class="fairing right"
      d="m-24.70498,81.16808l37.13758,-8.58557l148.8624,0l0,43l-186,0l0,-34.41443z"
      stroke-width="1.5"
    />
    <path
      class="fairing left"
      d="m4.795,38.22012l8.18624,-37.13758l32.81375,0l0,186l-41,0l0,-148.8624z"
      stroke-width="1.5"
    />
    <rect class="spacecraft-body" height="61" width="87" y="186.5" x="4" />
  </g>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Fire from './Fire.vue';

export default defineComponent({
  name: 'SecondStage',
  components: {
    Fire,
  },
});
</script>

<style>
g.stage-2 {
  transform: translate(-36px, -85px) scale(0.08);
}

g.stage-2 .tank {
  stroke: #000;
  fill: #fff;
}

g.stage-2 .fire {
  visibility: hidden;
}

.fairing {
  stroke: #000;
  fill: #fff;
}

g.launched .stage-2 {
  animation-name: ride-first-stage, second-stage-burn, orbit, de-orbit, fade-out;
  animation-duration: 1s, 2s, 6s, 3s, 1s;
  animation-timing-function: linear;
  animation-fill-mode: forwards;
  animation-iteration-count: 1, 1, 2.4, 1, 1;
  animation-delay: 1ms, 1s, 3s, 12s, 17s;
}

g.launched .stage-2 .fire {
  animation-name: ignition, re-entry, landing;
  animation-duration: 3s, 0.8s, 1s;
  animation-timing-function: linear;
  animation-fill-mode: forwards;
  animation-delay: 1.2s, 12.6s, 14s;
  animation-direction: normal;
}

g.launched .fairing {
  animation-duration: 2s, 2s;
  animation-timing-function: linear, linear;
  animation-fill-mode: forwards;
  animation-delay: 6s, 9s;
  animation-direction: normal, reverse;
}

g.launched .left {
  animation-name: open-left-fairing, open-lefty-fairing;
}

g.launched .right {
  animation-name: open-right-fairing, open-righty-fairing;
}

.fairing.right {
  transform: rotate(90deg) translate(27px, -165px);
}

.spacecraft-body {
  stroke: #000;
  fill: #555;
}

@keyframes ride-first-stage {
  0% {
    transform: translate(-36px, -85px) scale(0.08);
  }
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
  0% {
    transform: translate(40px, -124px) scale(0.08) rotate(65deg);
  }
  25% {
    /* burn to orbit */
    transform: translate(93px, -124px) scale(0.08) rotate(90deg);
  }
  50% {
    transform: translate(135px, -90px) scale(0.08) rotate(137deg);
  }
  75% {
    transform: translate(146px, -38px) scale(0.08) rotate(166deg);
  }
  99% {
    transform: translate(151px, 0px) scale(0.08) rotate(180deg);
  }
  100% {
    transform: translate(151px, 0px) scale(0.08) rotate(180deg);
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
  0% {
    transform: rotate(180deg) translateX(151px) scale(0.08) rotateZ(180deg);
  }
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

@keyframes open-lefty-fairing {
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

@keyframes open-righty-fairing {
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

@keyframes re-entry {
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

@keyframes landing {
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
