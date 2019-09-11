<template>
  <div class="app">
    <div class="panel">
      <Roulette v-bind:spin="rouletteSpin" />
      <Legend />
    </div>
    <button class="play-button" v-on:click="play()">PLAY</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Roulette from "./components/Roulette.vue";
import Legend from "./components/Legend.vue";

@Component({
  components: {
    Roulette,
    Legend
  }
})
export default class App extends Vue {
  rouletteSpin = false;
  play() {
    this.rouletteSpin = true;
  }
}
</script>

<style scoped lang="scss">
.app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.panel {
  display: flex;
  justify-content: space-evenly;
  align-items: center;

  .play-button {
    display: block;
  }
}
</style>
