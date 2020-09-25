<template>
  <rect class="rocket-pad" width="10" height="10" :x="x" :y="y"></rect>
</template>

<script>
export default {
  name: 'LaunchLandingPad',
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
};
</script>

<style scoped>
.rocket-pad {
  stroke: #8c8686;
  fill: #939393;
  stroke-width: 2.5px;
  transform: skew(25deg, -13deg);
}
</style>
