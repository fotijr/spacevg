<template>
  <g class="sat" x="0" y="0">
    <rect
      class="solar-panel"
      width="3.5"
      height="6"
      x="9"
      y="0"
    ></rect>
    <rect class="body" width="9" height="6"></rect>
  </g>
</template>

<script>
export default {
  name: 'Satellite',
};
</script>

<style scoped>
.sat {
  animation-duration: 6.25s, 5s, 6s;
  animation-delay: 0s, 6s, 11s;
  animation-name: delay-show, orbit-raising, leo;
  animation-iteration-count: 1, 1, infinite;
  animation-timing-function: linear, linear;
  animation-fill-mode: forwards;
  visibility: hidden;
  stroke-width: 0.25px;

  & .body {
    fill: #668879;
    stroke: #3d4d4a;
  }

  & .solar-panel {
    stroke: #f3c4ab;
    fill: #c1681a;
    /* Folded height of solar panel */
    height: 6px;
    animation-name: deploy-solar-panel;
    animation-delay: 9s;
    animation-duration: 3s;
    animation-fill-mode: forwards;
  }
}

@keyframes deploy-solar-panel {
  to {
    /* height of deployed panel */
    height: 13px;
    transform: rotateZ(-45deg) translate(-6px, 8px);
  }
}

@keyframes delay-show {
  99% {
    visibility: hidden;
  }
  100% {
    visibility: visible;
    transform: rotate(172deg) translateX(151px) rotateZ(90deg);
  }
}

@keyframes orbit-raising {
  0% {
    transform: rotate(172deg) translateX(151px) rotateZ(90deg);
  }
  55% {
    transform: rotate(355deg) translateX(151px) rotateZ(90deg);
  }
  75% {
    transform: rotate(425deg) translateX(165px) rotateZ(45deg);
  }
  100% {
    transform: rotate(515deg) translateX(175px);
  }
}

@keyframes leo {
  from {
    transform: rotate(155deg) translateX(175px);
  }
  to {
    transform: rotate(515deg) translateX(175px);
  }
}
</style>
