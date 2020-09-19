<template>
  <g class="sat" x="0" y="0">
    <rect width="10" height="6"></rect>
  </g>
</template>

<script>
export default {
  name: 'Satellite',
};
</script>

<style scoped>
.sat {
  fill: #f29885;
  animation-duration: 6.25s, 5s, 6s;
  animation-delay: 0s, 6s, 11s;
  animation-name: delay-show, orbit-raising, leo;
  animation-iteration-count: 1, 1, infinite;
  animation-timing-function: linear, linear;
  animation-fill-mode: forwards;
  visibility: hidden;
}

@keyframes delay-show {
  99% {
    visibility: hidden;
  }
  100% {
    visibility: visible;
    transform: rotate(175deg) translateX(151px);
  }
}

@keyframes orbit-raising {
  0% {
    transform: rotate(175deg) translateX(151px);
  }
  55% {
    transform: rotate(355deg) translateX(151px);
  }
  75% {
    transform: rotate(445deg) translateX(165px);
  }
  100% {
    transform: rotate(535deg) translateX(175px);
  }
}

@keyframes leo {
  from {
    transform: rotate(175deg) translateX(175px);
  }
  to {
    transform: rotate(535deg) translateX(175px);
  }
}
</style>
