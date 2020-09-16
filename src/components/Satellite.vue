<template>
  <g class="sat" x="0" y="0">
    <rect width="10" height="6"></rect>
  </g>
</template>

<script lang="ts">
export default {
  name: 'Satellite',
  props: {
    msg: String,
  },
  data() {
    return {
      count: 0,
    };
  },
};
</script>

<style scoped>
.sat {
  fill: #f29885;
  animation-duration: 6.25s, 6s, 6s;
  animation-name: delay-show, orbit-raising, leo;
  animation-iteration-count: 1, 1, infinite;
  animation-timing-function: linear, linear, linear;
  animation-fill-mode: both;
  visibility: hidden;
}

@keyframes delay-show {
  99% {
    visibility: hidden;
  }
  100% {
    visibility: visible;
    transform: rotate(175deg) translateX(121px);
  }
}

@keyframes orbit-raising {
  0% {
    fill: green;
    transform: rotate(175deg) translateX(121px);
  }
  50% {
    transform: rotate(255deg) translateX(145px);
  }
  100% {
    transform: rotate(535deg) translateX(175px);
  }
}

@keyframes leo {
  from {
    fill: yellow;
    transform: rotate(175deg) translateX(175px);
  }
  to {
    transform: rotate(535deg) translateX(175px);
  }
}
</style>
