<template>
  <g class="fire" :transform="`translate(${x},${y})`">
    <rect class="flame" y="15"></rect>
    <rect class="flame" x="18" y="15"></rect>
    <rect class="flame" x="36" y="15"></rect>
    <rect class="flame" x="54" y="15"></rect>
    <rect class="flame" x="72" y="15"></rect>
  </g>
</template>

<script lang="ts">
export default {
  name: 'Fire',
  props: {
    x: {
      type: Number,
      default: 0,
    },
    y: {
      type: Number,
      default: 0,
    },
  },
  setup(options) {
    // const root = document.documentElement;
    // root.style.setProperty('--mouse-x', e.clientX + 'px');
    // root.style.setProperty('--mouse-y', e.clientY + 'px');
  },
  data() {
    return {
      count: 0,
    };
  },
};
</script>

<style scoped>
.fire {
  height: 100px;
  width: 100px;
  border-bottom-width: var(--x);
}

.flame {
  fill: red;
  width: 18px;
  animation: flame-flicker 1.25s steps(25, end) 0s infinite;
}

.flame:nth-child(1) {
  animation-duration: 1.9s;
}

.flame:nth-child(2) {
  animation-duration: 2s;
}

.flame:nth-child(3) {
  animation-duration: 2.3s;
}

.flame:nth-child(4) {
  animation-duration: 2.4s;
}

.flame:nth-child(5) {
  animation-duration: 2.1s;
}

@keyframes flame-flicker {
  0% {
    height: 60px;
  }
  4% {
    height: 50px;
  }
  8% {
    height: 40px;
  }
  12% {
    height: 30px;
  }
  16% {
    height: 28px;
  }
  20% {
    height: 30px;
  }
  24% {
    height: 40px;
  }
  28% {
    fill: #fc4503;
    height: 32px;
  }
  32% {
    height: 40px;
  }
  36% {
    height: 60px;
  }
  40% {
    height: 28px;
  }
  44% {
    height: 40px;
  }
  48% {
    height: 70px;
  }
  52% {
    fill: #fc4103;
    height: 30px;
  }
  56% {
    height: 20px;
  }
  60% {
    height: 30px;
  }
  64% {
    height: 50px;
  }
  68% {
    height: 60px;
  }
  72% {
    fill: #fc8803;
    height: 70px;
  }
  76% {
    height: 80px;
  }
  80% {
    fill: #fcca03;
    height: 70px;
  }
  84% {
    height: 60px;
  }
  88% {
    fill: #fc8803;
    height: 50px;
  }
  92% {
    height: 60px;
  }
  96% {
    fill: #e84600;
    height: 70px;
  }
  100% {
    height: 80px;
  }
}
</style>
