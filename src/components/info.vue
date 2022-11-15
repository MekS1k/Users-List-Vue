<template>
  <div class="infoProg">
    <p>Картотека юзеров v 1.0.1</p>
    <a href="https://github.com/MekS1k" target="_blank"
      >https://github.com/MekS1k</a
    >
  </div>
</template>
<script>
export default {
  mounted() {
    this.$store.state.activeMain = 0;
    this.$store.state.activeInfo = 1;
    this.$store.state.activeSearch = 0;
  },
};
</script>

<style>
.infoProg {
  margin: 0 auto;
  text-align: center;
}
</style>
