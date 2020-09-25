<template>
  <div class="controls">
    <h1>SpaceVG</h1>
    <h5>
      <a
        href="https://github.com/fotijr/spacevg"
        target="_blank"
        title="View source code"
        >GitHub</a
      >
    </h5>
    <button class="launch" @click="launch" :disabled="launched">Launch</button>
    <ul>
      <li v-for="sat in satellites">
        {{ sat.name }} <a href="#" @click="deorbit(sat)">Deorbit</a>
      </li>
    </ul>
  </div>
  <div v-for="star in Array(30)" class="star"></div>
  <svg
    viewBox="0 0 400 400"
    preserveAspectRatio="xMidYMid meet"
    width="20"
    height="20"
  >
    <g class="orbit" :class="{ launched }">
      <g class="earth">
        <g>
          <circle
            r="120"
            cy="0"
            cx="0"
            stroke-width="0"
            stroke="#fff"
            fill="#9ACEE6"
          />
          <path
            d="m-10,20c-1,0 -4,-1 -7,-3c-3,-2 -5.31,-1.33749 -8,-3c-1.203,-0.7435 -5,-2 -7,-3c-2,-1 -5,-2 -7,-3c-2,-1 -4.85272,-2.1731 -6,-3c-1.814,-1.30746 -3.41885,-0.41885 -5,-2c-1.58115,-1.58115 -3,-2 -4,-3c-1,-1 -2.48627,-1.82376 -3,-4c-0.22977,-0.97324 -1,-3 -1,-4c0,0 0,-1 0,-2c0,-1 -0.32037,-2.02582 0,-4c0.50653,-3.12144 1.95517,-5.54915 3,-9c0.86935,-2.87128 0.78986,-5.07843 2,-8c0.85571,-2.06586 1.69254,-5.186 3,-7c0.8269,-1.14726 2,-2 3,-3c1,-1 1,-2 2,-3c1,-1 2,-3 3,-4c1,-1 3,-3 4,-4c1,-1 1.69345,-2.4588 3,-3c0.92389,-0.38269 1.69345,-1.4588 3,-2c0.92389,-0.38269 2,-1 3,-1c0,0 1,0 2,0c1,0 3,-1 4,-1c2,0 5,0 7,0c2,0 4,0 6,0c2,0 4,0 5,0c0,0 1,0 2,0c1,0 2,0 3,0c0,0 1,1 2,1c2,0 2,1 3,1c1,0 2,1 3,1c1,0 1.29291,-0.70711 2,0c0.70709,0.70711 1,1 1,1c1,0 1,1 1,1c1,0 1,0 2,0c0,0 1,0 1,0c1,0 2,0 3,-1c1,-1 2,-2 3,-2c1,0 1.29291,-0.29289 2,-1c0.70709,-0.70711 1.69345,-0.4588 3,-1c0.92389,-0.38269 3,0 3,0c1,0 2,0 3,0c0,0 1,0 3,0c1,0 2,0 3,0c1,0 2,0 4,0c1,0 1,1 2,1c1,0 2,1 2,1c1,0 2.29291,0.29289 3,1c0.70709,0.70711 0,1 1,1c0,0 -0.38269,1.07613 0,2c0.5412,1.30656 2,1 3,2c1,1 1.69345,2.4588 3,3c0.92389,0.38269 2,1 2,1c1,1 1.29291,2.29289 2,3c0.70709,0.70711 1,1 1,2c0,0 0,1 0,1c0,1 0,2 0,2c0,1 0,2 0,3c0,0 -0.49622,1.90779 -1,6c-0.36655,2.97752 -0.48627,4.82375 -1,7c-0.4595,1.9465 0,3 0,4c0,0 -0.29291,0.29289 -1,1c-0.70709,0.70711 0.38269,3.07613 0,4c-0.5412,1.30656 -1,2 -1,2c0,1 0,2 0,2c0,1 0,1 0,3c0,1 -0.76538,4.15225 0,6c0.5412,1.30655 1,2 1,3c0,1 0.4588,1.69345 1,3c0.38269,0.92389 0.48627,1.82376 1,4c0.22977,0.97324 0.61731,2.07611 1,3c0.5412,1.30655 0.56952,3.133 2,7c0.77579,2.09717 1.48627,3.82376 2,6c0.22977,0.97324 0.5405,3.0535 1,5c0.51373,2.17624 1,4 1,5c0,2 0.4588,1.69345 1,3c0.38269,0.92389 0,1 0,2c0,0 -1,1 -2,2c-1,1 -3,1 -5,2c0,0 -1,0 -1,0c-1,0 -2,0 -3,0c-2,0 -4,0 -5,0c-2,0 -3,0 -3,0c-1,0 -1,0 -2,0c-1,0 -2.82376,-0.48627 -5,-1c-0.97324,-0.22977 -2,0 -2,0c-1,0 -1,0 -1,-1c0,0 -0.29291,-0.29291 -1,-1c-0.70709,-0.70709 -1,-1 -1,-1c0,-1 0,-2 0,-2c0,-1 -0.29291,-1.29291 -1,-2c-0.70709,-0.70709 -2.4588,-0.69345 -3,-2c-0.38269,-0.92389 -1,-1 -1,-1c0,0 -1,0 -1,0c-1,0 -2.02676,0.22977 -3,0c-2.17624,-0.51373 -3.07611,-0.61731 -4,-1c-1.30655,-0.5412 -2,-1 -2,-1c-1,-1 -2,-1 -2,-1c-1,0 -2.29291,-0.29291 -3,-1c-0.70709,-0.70709 -1,-1 -2,-1c-1,0 -2,0 -3,-1c0,0 -1.29291,0.70709 -2,0c-0.70709,-0.70709 -1,-1 -1,-1c0,0 -1,0 -2,0c-1,0 -2,0 -3,-1c0,0 -1,0 -1,0c-1,0 -2.07611,0.38269 -3,0c-1.30655,-0.5412 -2,-1 -3,-1c-1,0 -1,-1 -1,-1c0,-1 0,-2 0,-2c0,0 0,-1 0,-1c0,0 -1.07611,-0.61731 -2,-1c-1.30655,-0.5412 -1,-1 -1,-1c-1,0 -1,0 -2,0c0,0 -1,0 -1,0c0,0 -1,0 -2,1l0,1"
            stroke-width="0"
            fill="#559E84"
          />
        </g>
      </g>
      <Satellite v-for="sat in satellites" />
      <LaunchLandingPad :x="-28" :y="-25" />
      <LaunchLandingPad :x="44" :y="-10" />
      <SecondStage />
      <FirstStage />
    </g>
  </svg>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import FirstStage from './FirstStage.vue';
import SecondStage from './SecondStage.vue';
import Satellite from './Satellite.vue';
import LaunchLandingPad from './LaunchLandingPad.vue';

export default defineComponent({
  name: 'PlanetEarth',
  components: {
    Satellite,
    FirstStage,
    SecondStage,
    LaunchLandingPad,
  },
  data() {
    return {
      satellites: [],
      launched: false,
    };
  },
  methods: {
    launch() {
      const sat = {
        name: `Sat-${this.satellites.length + 1}`,
      };
      setTimeout(() => {
        this.launched = false;
      }, 20000);
      this.satellites.push(sat);
      this.launched = true;
    },
    deorbit(sat) {
      const index = this.satellites.indexOf(sat);
      if (index >= 0) {
        this.satellites.splice(index, 1);
      }
    },
  },
});
</script>

<style>
button {
  padding: 5px 10px;
}

div.controls {
  position: absolute;
  top: 15px;
  left: 15px;
}

li a {
  visibility: hidden;
}

li:hover a {
  visibility: visible;
}

svg {
  width: 100%;
  height: 100%;
  /* Prevent stars from showing on top of earth or spacecraft */
  z-index: 1;
  pointer-events: none;
}

g.orbit {
  transform: translate(200px, 200px);
}

button.launch {
  letter-spacing: 2px;
  text-transform: uppercase;
}

g.processing {
  visibility: hidden;
}

.star {
  position: absolute;
  background-color: #fff;
  height: 1px;
  width: 1px;

  @for $i from 1 to 30 {
    top: percentage(random(100));
    left: percentage(random(100));
    &:nth-child($i) {
      top: percentage(random(100));
      left: percentage(random(100));
    }
  }
}
</style>
