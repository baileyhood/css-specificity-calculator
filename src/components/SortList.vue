<template>
  <div>
    <button v-on:click="sortList">Sort List</button>
  </div>
</template>

<script>
export default {
  props: ["selectorList"],

  methods: {
    sortedList: function() {
      this.$emit("update-list", this.sortList());
    },

    sortList: function() {
      window.console.log(this.selectorList);
    }
  }
};
</script>