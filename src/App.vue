<template>
  <PlanetEarth />
</template>

<script lang="ts">
import PlanetEarth from './components/PlanetEarth.vue';
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'App',
  components: {
    PlanetEarth,
  }
});
</script>
