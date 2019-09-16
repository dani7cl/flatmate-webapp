<template>
  <div class="roulette">
    <div class="pie">
      <div class="spinner" ref="spinner">
        <div class="segment"></div>
        <div class="segment"></div>
        <div class="segment"></div>
      </div>
      <p class="name">Dani</p>
      <p class="name">Jose</p>
      <p class="name">Lorena</p>
      <p class="name">Alba</p>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class Roulette extends Vue {
  private intervalRef: number = 0;

  public startSpinning() {
    const draw = (progress: number) => {
      (this.$refs.spinner as any).style.transform =
        "rotate(" + progress * 360 + "deg)";
    };
    this.animate({
      loopTime: 500,
      maxDuration: 2750,
      draw
    });
  }

  private animate({
    draw,
    loopTime,
    maxDuration
  }: {
    draw: (progress: number) => void;
    loopTime: number;
    maxDuration: number;
  }) {
    const start = performance.now();
    requestAnimationFrame(function animate(time) {
      const progress = (time - start) / loopTime;
      if (time - start < maxDuration) {
        draw(progress);
        requestAnimationFrame(animate);
      }
    });
  }
}
</script>

<style scoped lang="scss">
.roulette {
  display: inline-block;
}
.pie {
  height: 500px;
  width: 500px;
  border-radius: 50%;
  background: #d1cfc0;
  position: relative;
  overflow: hidden;
  .spinner {
    width: 100%;
    height: 100%;
    transition: transform 0.5s linear;
  }
}
.segment {
  position: absolute;
  height: 100%;
  width: 100%;
  &:first-child {
    background: #f4f186;
    transform: translate(50%, -50%);
  }

  &:nth-child(2) {
    background: #90ee90;
    transform: translate(-50%, 50%);
  }

  &:nth-child(3) {
    background: #add8e6;
    transform: translate(50%, 50%);
  }

  @keyframes rotate {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
}
.name {
  position: absolute;
  top: 30%;
  left: 50%;
  width: 50%;
  text-align: center;
  margin: 0;
  font-weight: bold;
  &:nth-of-type(2) {
    left: 0%;
  }
  &:nth-of-type(3) {
    top: 70%;
  }
  &:nth-of-type(4) {
    top: 70%;
    left: 0%;
  }
}
</style>
