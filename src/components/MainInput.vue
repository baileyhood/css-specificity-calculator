<template>
  <div>
    <input v-model="inputText" placeholder="Enter selector" type="text">
    <button v-on:click="showText" type="submit">Submit</button>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      inputText: ""
    };
  },

  methods: {
    showText: function() {
      alert(this.inputText);
    }
  }
};
</script>
