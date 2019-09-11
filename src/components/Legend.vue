<template>
  <div class="legend">
    <div class="task">
      <div class="square gray"></div>
      <span>Cuina</span>
    </div>
    <div class="task">
      <div class="square yellow"></div>
      <span>Menjador</span>
    </div>
    <div class="task">
      <div class="square green"></div>
      <span>Treure Brossa</span>
    </div>
    <div class="task">
      <div class="square blue"></div>
      <span>Passadís</span>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Legend extends Vue {}
</script>

<style scoped lang="scss">
.legend {
  display: inline-block;

  .task {
    display: table;
    span {
      display: table-cell;
      vertical-align: middle;
    }
  }
  .square {
    width: 30px;
    height: 30px;
    display: inline-block;
    margin-right: 10px;
    &.gray {
      background-color: #d1cfc0;
    }

    &.yellow {
      background-color: #f4f186;
    }

    &.green {
      background-color: #90ee90;
    }

    &.blue {
      background-color: #add8e6;
    }
  }
}
</style>
