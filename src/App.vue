<template>
  <div id="app">
    <h1>CSS Specificity</h1>
    <p>Not only is “CSS specificity” hard to say, but it can be difficult to understand. Use the calculator below to learn what your CSS selector’s specificity level is.</p>
    <MainInput/>
  </div>
</template>

<script>
import MainInput from "./components/MainInput.vue";

export default {
  //Name of the component used in main.js
  name: "app",
  components: {
    MainInput
  }
};
</script>

<style lang="scss">
@import "assets/styles/project";
</style>
