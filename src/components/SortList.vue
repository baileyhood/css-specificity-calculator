<template>
  <div>
    <button class="button button--sort" v-on:click="sortList">Sort List</button>
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
      this.selectorList.sort(function(a, b) {
        return a.specificityNumber - b.specificityNumber;
      });
    }
  }
};
</script>