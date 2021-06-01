<template>
  <div class="container mx-auto mt-3 items-center justify-center">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
