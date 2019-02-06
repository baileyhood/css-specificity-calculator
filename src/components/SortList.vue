<template>
  <div>
    <button v-on:click="sortList">Sort List</button>
  </div>
</template>

<script>
export default {
  props: ["selectorList"],

  methods: {
    sortList: function() {
      this.selectorList.forEach(el => {
        window.console.log(el);
      });
    }
  }
};
</script>