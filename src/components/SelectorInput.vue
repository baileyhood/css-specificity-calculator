<template>
  <div>
    <h3 class="c-subheadline">ENTER YOUR SELECTOR BELOW</h3>
    <!-- NOTE: v-model allows two-way data-binding: model & view are both updated together (keeps each in sync) -->
    <div class="c-input__container">
      <input class="c-input__item" v-model="selectorText" placeholder="Enter selector" type="text">
      <button class="c-input__button" v-on:click="addSelectorToList" type="submit">Submit</button>
    </div>
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
      const split = this.selectorText.split(/\s|(?=\.)|(?=#)/); //separate into strings
      const selectorObj = {};

      this.getSpecificityNumber(split, selectorObj); //assign specificity numbers
      selectorObj.entireSelector = this.selectorText; //add entire selector to obj
      return selectorObj;
    },

    assignSpecificityNumber: function(type, obj) {
      obj[type] = obj[type] >= 1 ? obj[type] + 1 : 1;
    },

    // TODO: account for combinator selectors. Possibly try RegEx
    getSpecificityNumber: function(splitArr, obj) {
      const vm = this;
      splitArr.forEach(function(selector) {
        if (selector.indexOf(".") === 0) {
          vm.assignSpecificityNumber("class", obj);
        } else if (selector.indexOf("#") === 0) {
          vm.assignSpecificityNumber("id", obj);
        } else {
          vm.assignSpecificityNumber("element", obj);
        }
      });
    }
  } //methods
}; //export default
</script>
