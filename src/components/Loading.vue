<template>
  <div class="loading_wrapper">
    <div class="ring_wrapper">
      <div class="background_ring"></div>
      <div class="progress"></div>
      <div class="inner"></div>
    </div>
    <div class="loading_label">{{ progressPercentage }}%</div>
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
      if (progressNumber > 100) return progressNumber;
      else return progressNumber * 100;
    }
  }
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
    border-radius: 100%;
    overflow: hidden;
    position: relative;
    .background_ring {
      border: 30px solid $gray;
      border-radius: 100%;
      height: 10rem;
      width: 10rem;
    }
    .progress {
      background-color: $blue;
      inset: 0 0 50% 50%;
      position: absolute;
      &::before, &::after {
        background-color: $blue;
        border-radius: 100%;
        content: "";
        height: 30px;
        position: absolute;
        width: 30px;
      }
      &:before {
        left: 0;
        top: 0;
        transform: translateX(-40%);
      }
      &::after {
        right: 0;
        bottom: 0;
        transform: translatey(40%);
      }
    }
    .inner {
      background-color: white;
      border-radius: 100%;
      inset: 30px;
      position: absolute;
    }
  }
  .loading_label {
    color: #333333;
    font-family: "Fira", "Times New Roman", sans-serif;
    left: 50%;
    position: absolute;
    top: 50%;
    transform: translate(-50%, -50%);
  }
</style>
