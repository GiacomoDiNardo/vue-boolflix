<template>
  <div>
    <input type="text" v-model="searchText">
    <button @click="startSearch">Cerca</button>
  </div>
</template>

<script>

export default {
  data() {
    return {
      searchText: ""
    }
  },

  methods: {
    startSearch() {
      this.$emit("searchingText", this.searchText)
    },
  }

}
</script>

<style>

</style>