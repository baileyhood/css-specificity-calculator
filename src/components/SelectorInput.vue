<template>
  <div>
    <div class="h-flex h-align-items-center h-justify-content-space-between">
      <h3 class="c-subheadline">ENTER YOUR SELECTOR BELOW</h3>
      <sort-list v-bind:selectorList="selectorList"></sort-list>
    </div>

    <!-- NOTE: v-model allows two-way data-binding: model & view are both updated together (keeps each in sync) -->
    <div class="c-input__container">
      <input
        class="c-input__item"
        v-model="selectorText"
        @keyup.enter="addSelectorToList"
        placeholder="Enter selector"
        type="text"
      >
      <button class="c-input__button" v-on:click="addSelectorToList" type="submit">Submit</button>
    </div>
    <selector-list v-bind:selectorList="selectorList"></selector-list>
  </div>
</template>

<script>
import SelectorList from "./SelectorList.vue";
import SortList from "./SortList.vue";

export default {
  components: {
    "selector-list": SelectorList,
    "sort-list": SortList
  },

  data: function() {
    return {
      selectorText: "",
      selectorList: []
    };
  },

  methods: {
    addSelectorToList: function() {
      //only when text has been entered
      if (this.selectorText) {
        this.selectorList.push(this.getSpecificity());
        this.selectorText = ""; //clear input
      }
    },

    getSpecificity: function() {
      const split = this.selectorText.split(/\s|(?=\.)|(?=#)/); //separate into strings by " ", "#" and "."
      const selectorObj = {};

      this.getSpecificityNumber(split, selectorObj); //assign specificity numbers
      selectorObj.entireSelector = this.selectorText; //add entire selector to obj
      selectorObj.specficityNumber = `${selectorObj.id ||
        0}${selectorObj.class || 0}${
        selectorObj.element || 0 //add entire specicifty number to obj to pass to sortList component
      }`;
      return selectorObj;
    },

    assignSpecificityNumber: function(type, obj) {
      obj[type] = obj[type] >= 1 ? obj[type] + 1 : 1;
    },

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
