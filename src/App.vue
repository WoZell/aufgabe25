<template>
  <div class="main_container">
    <Loading :progress="progress"/>
    <div class="plus" @click="progress < 100 ? progress += 25 : null"></div>
    <div class="minus" @click="progress > 0 ? progress -= 25 : null"></div>
  </div>
</template>

<script lang="ts">
import Loading from "@/components/Loading.vue";

export default {
  components: {
    Loading,
  },
  data() {
    return {
      progress: 25
    };
  }
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
    position: relative;
    width: 100%;
  }
  .plus, .minus {
    bottom: 0;
    height: 100%;
    position: absolute;
    top: 0;
    width: 20%;
  }
  .minus { left: 0; }
  .plus { right: 0; }
</style>
