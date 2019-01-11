<template>
  <div>
    <ul>
      <li v-for="(selector, index) in selectorList" v-bind:key="index">
        {{selector}}
        <span class="id-count"></span>
        <span class="class-count"></span>
        <span class="element-count"></span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["selectorList"]
};
</script>