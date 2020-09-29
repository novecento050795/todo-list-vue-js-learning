<template>
    <li>
      <span 
        :class="{
          done: todo.completed
        }"
      >
        <input 
          type="checkbox" 
          @change="todo.completed = !todo.completed"
        >
        <strong>{{index + 1}}</strong>
        {{todo.text}}
      </span>
      <button
        class='rm'
        @click="$emit('remove-item', todo.id)"
      >
        &times;
      </button>
    </li>
</template>

<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true
      },
      index: {
        type: Number,
        required: true
      }
    }
  }
</script>

<style scoped>
  .done {
      text-decoration: line-through;
  }
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
  }
  .rm {
    background: red;
    color: #fff;
    border-radius: 50%;
    font-weight: bold;
  }
  input {
    margin-right: 1rem;
  }
</style>