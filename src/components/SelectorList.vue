<template>
  <div>
    <ul v-if="selectorList.length" class="c-input__list h-margin-top-0">
      <li class="c-input__list-item" v-for="(selector, index) in selectorList" v-bind:key="index">
        {{selector.entireSelector}}
        <div class="c-input__selector">
          <span v-if="selector.id" class="id-count">{{selector.id}}</span>
          <span v-else class="id-count">0</span>
          
          <span v-if="selector.class" class="class-count">{{selector.class}}</span>
          <span v-else class="class-count">0</span>
          
          <span v-if="selector.element" class="element-count">{{selector.element}}</span>
          <span v-else class="element-count">0</span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["selectorList"]
};
</script>