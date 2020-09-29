<template>
  <div>
    <ul>
      <TodoItem
        v-for="(todo, index) in todos"
        :todo="todo"
        :key="todo.id"
        :index="index"
        @remove-item="id => $emit('remove-item', id)"
      />
    </ul>
  </div>
</template>

<script>

  import TodoItem from './TodoItem'
  import AddItem from './AddItem'

  export default {
    props: {
      todos: {
        type: Array
      }
    },
    components: {
      TodoItem,
      AddItem
    },
    methods: {
    }
  }

</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>