<template>
  <div class="main_container">
    <Loading/>
  </div>
</template>

<script lang="ts">
import Loading from "@/components/Loading.vue";

export default {
  components: {
    Loading,
  },
};
</script>

<style lang="scss">
  @import "assets/typo.css";
  @import "assets/reset";
  .main_container {
    background-color: #fafafa;
    display: grid;
    min-height: 100vh;
    place-content: center;
    width: 100%;
  }
</style>
