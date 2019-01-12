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
      this.selectorList.push(this.getSpecificity());
      this.selectorText = "";
    },

    getSpecificity: function() {
      const split = this.selectorText.split(" "); //separate into strings
      const selectorObj = {};

      this.assignNumber(split, selectorObj); //assign specificity numbers
      selectorObj.entireSelector = this.selectorText; //add entire selector to obj
      return selectorObj;
    },

    assignNumber: function(splitArr, obj) {
      splitArr.forEach(function(el) {
        if (el.indexOf(".") === 0) {
          obj.class = obj.class >= 1 ? obj.class + 1 : 1;
        } else if (el.indexOf("#") === 0) {
          obj.id = obj.id >= 1 ? obj.id + 1 : 1;
        } else {
          obj.element = obj.element >= 1 ? obj.element + 1 : 1;
        }
      });
    }
  }
};
</script>
