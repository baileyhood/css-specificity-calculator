<template>
  <div>
    <h3 class="c-subheadline">ENTER YOUR SELECTOR BELOW</h3>
    <!-- NOTE: v-model allows two-way data-binding: model & view are both updated together (keeps each in sync) -->
    <input v-model="selectorText" placeholder="Enter selector" type="text">
    <button v-on:click="addSelectorToList" type="submit">Submit</button>
    <selector-list v-bind:selectorList="selectorList"></selector-list>
  </div>
</template>

<script>
import SelectorList from "./SelectorList.vue";

export default {
  components: {
    "selector-list": SelectorList
  },

  data: function() {
    return {
      selectorText: "",
      selectorList: []
    };
  },

  methods: {
    addSelectorToList: function() {
      this.checkSpecificity();
      this.selectorList.push(this.selectorText);
      this.selectorText = "";
    },
    checkSpecificity: function() {
      const split = this.selectorText.split(" ");
      split.forEach(function(el) {
        if (el.indexOf(".") === 0) {
          console.log("this is a class ", el);
        } else if (el.indexOf("#") === 0) {
          console.log("this is an id", el);
        } else {
          console.log("this is an element");
        }
      });
    },
    countSpecificity: function() {}
  }
};
</script>
