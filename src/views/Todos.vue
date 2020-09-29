<template>
  <div>
    <router-link to="/">Home</router-link>
    <AddItem
      @add-item="addItem"
    />
    <select v-model="filter">
      <option value="all">all</option>
      <option value="completed">completed</option>
      <option value="not-completed">not-completed</option>
    </select>
    <br/>
    <Loader v-if="loading" />
    <TodoList
      v-else-if="filteredItems.length"
      :todos="filteredItems"
      @remove-item="removeItem"
    />
    <p v-else>No Items!!!</p>
  </div>
</template>

<script> 

  import TodoList from '@/components/Todo/TodoList'
  import AddItem from '@/components/Todo/AddItem'
  import Loader from '@/components/Loader/Loader'

  export default {
    name: 'App',
    data() {
      return {
        todos: [
          {id: 1, text: 'text1', 'completed': false},
          {id: 2, text: 'text2', 'completed': false},
          {id: 3, text: 'text3', 'completed': false},
          {id: 4, text: 'text4', 'completed': false},
        ],
        loading: true,
        filter: 'all'
      }
    },
    components: {
      TodoList,
      AddItem,
      Loader,
    },
    computed: {
      filteredItems() {
        switch (this.filter){
          case 'all':
            return this.todos
          case 'completed':
            return this.todos.filter(todo => todo.completed)
          case 'not-completed':
            return this.todos.filter(todo => !todo.completed)
        }
      }
    },
    mounted() {
      setTimeout( () => this.loading = false, 2000)
    },
    methods: {
      removeItem(todo_id) {
        this.todos = this.todos.filter(t => t.id !== todo_id)
      },
      addItem(text) {
        if (text.trim()) {
          this.todos.push({
            id: Date.now(),
            text:text,
            completed: false
          })
        }
      }
    }
  }

</script>