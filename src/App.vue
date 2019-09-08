<template>
  <Roulette/>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Roulette from './components/Roulette.vue';

@Component({
  components: {
    Roulette,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
body {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
