<template>
  <div>
    <p>Completed Tasks: {{ todos.filter(todo => {return todo.done === true}).length }} </p>
    <p>Pending Tasks: {{ todos.filter(todo => {return todo.done === false }).length }} </p>

    <todo 
      v-for="(todo, index) in todos"
      v-bind:todo="todo"
      v-bind:key="index"
      v-on:delete-todo="deleteTodo"
      v-on:complete-todo="completeTodo"
      v-on:uncomplete-todo="uncompleteTodo">
      </todo>

  </div>
</template>

<script>
  /* eslint-disable */
  import Todo from './Todo'

  export default {
    props: ['todos'],
    components : {
      Todo,
    },
    methods: {
      deleteTodo(todo) {
        const todoIndex = this.todos.indexOf(todo)
        this.todos.splice(todoIndex, 1)
      },
      completeTodo(todo) {
        const todoIndex = this.todos.indexOf(todo)
        this.todos[todoIndex].done = true
      },
      uncompleteTodo(todo) {
        const todoIndex = this.todos.indexOf(todo)
        this.todos[todoIndex].done = false
      }
    }
  } 

</script>

<style>

</style>


