<template>
  <div id="app">
    <h1 class="c-headline c-headline__divider">CSS Specificity</h1>
    <p>Not only is “CSS specificity” hard to say, but it can be difficult to understand. Use the calculator below to learn what your CSS selector’s specificity level is.</p>
    <selector-input class="h-margin-top-35"></selector-input>
  </div>
</template>

<script>
import SelectorInput from "./components/SelectorInput.vue";

export default {
  //Name of the component used in main.js
  name: "app",
  components: {
    "selector-input": SelectorInput
  }
};
</script>

<style lang="scss">
@import "assets/styles/project";

#app {
  margin-left: auto;
  margin-right: auto;
  max-width: 800px;
}
</style>
