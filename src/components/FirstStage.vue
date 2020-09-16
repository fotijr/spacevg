<template>
  <g class="stage-1">
    <rect
      id="tanks"
      height="440.99999"
      width="87.00001"
      y="3.5"
      x="4.5"
      stroke-width="0"
      fill="#dedede"
    />
    <Fire :x="0" :y="437" />
    <path
      class="bell"
      d="m51.5725,463.81247l7.5,-19l25.00001,0l7.5,19l-40.00001,0z"
    />
    <path
      class="bell"
      d="m6.5725,463.81247l7.5,-19l25.00001,0l7.5,19l-40.00001,0z"
    />
  </g>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Fire from './Fire.vue';

export default defineComponent({
  name: 'FirstStage',
  components: {
    Fire
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
g.stage-1 {
  transform: scale(0.08) translate(-450px, -630px);
}

g.launched .stage-1 {
  animation-name: launch, land;
  animation-duration: 1s, 1s;
  animation-timing-function: linear, linear;
  animation-fill-mode: forwards;
  animation-delay: 0s, 1.1s;
}

@keyframes launch {
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
  40% {
    transform: translate(44px, -84px) scale(0.08) rotate(33deg);
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
