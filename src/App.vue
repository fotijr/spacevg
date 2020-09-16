<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <PlanetEarth />
</template>

<script lang="ts">
import PlanetEarth from './components/PlanetEarth.vue';
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'App',
  components: {
    PlanetEarth,
  },
  setup() {
    // const launch = () => {
    //   count.value++;
    // };

    return {
      // launch
    };
  },
});
</script>

<style scoped></style>
