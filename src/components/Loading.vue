<template>
  <div class="loading_wrapper">
    <div class="background_ring"></div>
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
  .background_ring {
    border: 30px solid $gray;
    border-radius: 100%;
    height: 10rem;
    width: 10rem;
  }
  .loading_label {
    color: #333333;
    display: grid;
    font-family: "Fira", "Times New Roman", sans-serif;
    inset: 0;
    place-content: center;
    position: absolute;
  }
</style>
