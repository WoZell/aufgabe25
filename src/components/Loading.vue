<template>
  <div class="loading_wrapper">
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
  .loading_wrapper {
    background-color: white;
    border: 1px solid #efefef;
    height: 30rem;
    width: 30rem;
  }
  .loading_label {
    font-family: "Fira", "Times New Roman", sans-serif;
    color: #333333;
    letter-spacing: 0px;
  }
</style>
