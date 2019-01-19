<template>
  <div>
    <button v-on:click="sortList">Sort List</button>
  </div>
</template>

<script>
export default {
  props: ["selectorList"],

  methods: {
    //TODO: need to add entire specificity value to the selectorObj
    sortList: function() {
      this.selectorList.forEach(el => {
        window.console.log(el);
      });
    }
  }
};
</script>