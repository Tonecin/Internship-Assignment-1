<template>
    <div v-show="!deleted">
      <button @click="deleteActor">Delete</button>
      {{ actor }}
    </div>
  </template>
  
<script>
export default {
  data() {
    return {
      deleted: false
    }
  },
  props: ['actor'],
  methods: {
    deleteActor() {
      this.deleted = true
    }
  }
};
</script>
  
<style scoped>
</style>