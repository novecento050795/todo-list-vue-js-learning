<template>
  <form @submit.prevent="$emit('add-item', text)">
    <input type="text" v-model="text">
    <button>create</button>
  </form>
</template>

<script>

  export default {
    data() {
      return {
        text: ''
      }
    }
  }
</script>

<style scoped>
  form {
    display: flex;
    margin-bottom: 0.5rem;
  }
  input {
    width: 400px;
  }
</style>