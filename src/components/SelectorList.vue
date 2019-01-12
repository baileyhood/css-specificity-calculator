<template>
  <div>
    <ul>
      <li v-for="(selector, index) in selectorList" v-bind:key="index">
        {{selector.entireSelector}}
        <span v-if="selector.id" class="id-count">{{selector.id}}</span>
        <span v-else class="id-count">0</span>
        <span v-if="selector.class" class="class-count">{{selector.class}}</span>
        <span v-else class="class-count">0</span>
        <span v-if="selector.element" class="element-count">{{selector.element}}</span>
        <span v-else class="element-count">0</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["selectorList"]
};
</script>