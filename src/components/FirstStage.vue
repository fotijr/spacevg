<template>
  <g class="stage-1">
    <rect class="tanks" height="441" width="87" y="3.5" x="4.5" />
    <Fire :x="0" :y="437" />
    <path class="bell" d="m51.5725,463.81247l7.5,-19l25,0l7.5,19l-40,0z" />
    <path class="bell" d="m6.5725,463.81247l7.5,-19l25,0l7.5,19l-40,0z" />
  </g>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Fire from './Fire.vue';

export default defineComponent({
  name: 'FirstStage',
  components: {
    Fire,
  },
});
</script>

<style>
g.stage-1 {
  transform: scale(0.08) translate(-450px, -630px);
}

g.stage-1 .fire {
  visibility: hidden;
}

g.stage-1 .tanks {
  fill: #dedede;
  stroke: #d4d4d4;
  stroke-width: 0.25px;
}

g.launched .stage-1 {
  animation-name: launch, land, fade-out;
  animation-duration: 1s, 3s, 1s;
  animation-timing-function: linear;
  animation-fill-mode: forwards;
  animation-delay: 1ms, 1.1s, 17s;
  -webkit-animation-delay: 1ms, 1.1s, 17s;
  animation-play-state: running;
}

g.launched .stage-1 .fire {
  animation-name: liftoff, s1-landing;
  animation-duration: 1.0s, 1.7s;
  animation-timing-function: linear, linear;
  animation-fill-mode: forwards, forwards;
  animation-delay: 0s, 2.5s;
  animation-iteration-count: 1, 1;
  animation-direction: normal, normal;
  animation-play-state: running, running;
}

@keyframes liftoff {
  0% {
    visibility: hidden;
  }
  1% {
    visibility: visible;
  }
  99% {
    visibility: visible;
  }
  100% {
    visibility: hidden;
  }
}

@keyframes s1-landing {
  0% {
    visibility: hidden;
  }
  1% {
    visibility: visible;
  }
  99% {
    visibility: visible;
  }
  100% {
    visibility: hidden;
  }
}

@keyframes launch {
  0% {
    transform: scale(0.08) translate(-450px, -630px);
  }
  40% {
    /* max q */
    transform: translate(-10px, -75px) scale(0.08) rotate(30deg);
  }
  100% {
    /* MECO */
    transform: translate(10px, -110px) scale(0.08) rotate(65deg);
  }
}

@keyframes land {
  0% {
    transform: translate(10px, -110px) scale(0.08) rotate(65deg);
  }
  40% {
    transform: translate(44px, -84px) scale(0.08) rotate(33deg);
  }
  95% {
    /* Landed */
    transform: translate(43px, -59px) scale(0.08) rotate(0deg);
  }
  100% {
    /* Landed */
    transform: translate(43px, -53px) scale(0.08) rotate(0deg);
  }
}

path.bell {
  stroke-width: 0.5px;
  stroke: #999999;
  fill: #333333;
}
</style>
