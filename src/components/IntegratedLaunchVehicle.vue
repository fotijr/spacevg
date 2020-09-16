<template>
  <g class="integrated">
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
        transform="rotate(90, 68.295, 94.0825)"
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
        fill-opacity="null"
        stroke-opacity="null"
        stroke-width="1.5"
        stroke="#000"
        fill="#fff"
      />
    </g>
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
      <path
        class="bell"
        d="m51.5725,463.81247l7.5,-19l25.00001,0l7.5,19l-40.00001,0z"
      />
      <path
        class="bell"
        d="m6.5725,463.81247l7.5,-19l25.00001,0l7.5,19l-40.00001,0z"
      />
    </g>
  </g>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'IntegratedLaunchVehicle',
  setup() {
    const state = ref({
      launched: false,
      orbit: false,
    });
    const launch = () => {
      state.value.launched = true;

      setTimeout(() => {
        state.value.orbit = true;
      }, 3000);
    };

    return {
      launch,
      state,
    };
  },
});
</script>

<style scoped>
g.integrated {
  transform: translate(-40px, -50px) scale(0.2);
}

g.integrated.launched {
  animation: launch 1s linear;
  animation-fill-mode: forwards;
}

/* g.integrated.launched .stage-1 {
  animation: land 1s linear;
  animation-fill-mode: forwards;
  animation-delay: 1.2s;
} */

g.integrated.launched .stage-2 {
  animation: second-stage-burn 2s linear;
  animation-fill-mode: forwards;
  animation-delay: 1s;
}

@keyframes launch {
  40% {
    /* max q */
    transform: translate(-10px, -75px) scale(0.2) rotate(30deg);
  }
  100% {
    /* MECO */
    transform: translate(10px, -110px) scale(0.2) rotate(65deg);
  }
}

@keyframes land {
  100% {
    /* Landed */
    transform: translate(228px, -103px) scale(0.4) rotate(-65deg);
  }
}

@keyframes second-stage-burn {
  20% {
    /* burn to orbit */
    transform: translate(-36px, -202px) scale(0.4);
  }
  40% {
    transform: translate(-57px, -275px) scale(0.4);
  }
  100% {
    transform: translate(385px, -574px) rotate(73deg) scale(0.4);
  }
}

g.integrated.orbit .stage-2 {
  animation-duration: 6s;
  animation-name: orbit;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
  animation-fill-mode: both;
  transform-origin: center;
}

@keyframes orbit {
  0% {
    transform: translate(385px, -574px) rotate(0) scale(0.4);
  }
  100% {
    transform: translate(385px, -574px) rotate(360deg) scale(0.4);
  }
}

g.stage-2 {
  transform: translate(0, -177px) scale(0.4);
}

g.stage-1 {
  transform: scale(0.4);
}

path.bell {
  stroke-width: 2px;
  stroke: #999999;
  fill: #333333;
}
</style>
