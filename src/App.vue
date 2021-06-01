<template>
  <div class="flex flex-col mt-5">
    <Looper />
  </div>
</template>

<script>
import Looper from "./components/Looper.vue";

export default {
  name: "App",
  components: {
    Looper,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
