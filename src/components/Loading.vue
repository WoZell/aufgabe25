<template>
  <div class="loading_wrapper">
    <div class="ring_wrapper">
      <div :class="`progress${progressPercentage}`" class="progress"></div>
      <div v-if="progressPercentage === 75" class="progress_helper"></div>
      <div class="inner">{{ progressPercentage }}%</div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Loading",
  props: {
    progress: { type: [ Number, String ], default: .25 }
  },
  computed: {
    progressPercentage() {
      const progressNumber = typeof this.progress === "string" ? parseFloat(this.progress) : this.progress;
      return Math.round(progressNumber / 25) * 25;
    },
  },
});
</script>

<style lang="scss" scoped>
  @import "src/assets/variables";
  .loading_wrapper {
    background-color: white;
    border: 1px solid #efefef;
    display: grid;
    height: 30rem;
    place-content: center;
    position: relative;
    width: 30rem;
  }
  .ring_wrapper {
    background-color: $gray;
    border-radius: 100%;
    height: 10rem;
    overflow: hidden;
    position: relative;
    width: 10rem;
    .progress {
      background-color: $blue;
      position: absolute;
      &::before, &::after {
        background-color: $blue;
        border-radius: 100%;
        content: "";
        height: 30px;
        position: absolute;
        width: 30px;
      }
      &::before {
        left: 0;
        top: 0;
        transform: translateX(-40%);
      }
      &::after {
        bottom: 0;
        right: 0;
        transform: translatey(40%);
      }
    }
    .progress_helper {
      background-color: $blue;
      inset: 50% 50% 0 0;
      position: absolute;
      &::after {
        background-color: $blue;
        border-radius: 100%;
        bottom: 100%;
        content: "";
        height: 30px;
        left: 0;
        position: absolute;
        transform: translateY(40%);
        width: 30px;
      }
    }
    .progress0 { inset: 0 50% 50% 50%; }
    .progress25 { inset: 0 0 50% 50%; }
    .progress50, .progress75 {
      inset: 0 0 0 50%;
      &::after {
        bottom: 0;
        left: 0;
        transform: translateX(-40%);
      }
    }
    .progress100 { inset: 0 0 0 0; }
    .inner {
      background-color: white;
      border-radius: 100%;
      color: #333333;
      display: grid;
      font-family: "Fira", "Times New Roman", sans-serif;
      inset: 30px;
      place-content: center;
      position: absolute;
    }
  }
</style>
