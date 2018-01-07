<template>
  <div>
    <h1>TodoList</h1>
    <form @submit.prevent="addTodo(todoName)">
      <input type="text" v-model="todoName">
      <button type="submit">Submit</button>
    </form>

    <ul>
      <TodoItem v-for="todo in todos" v-bind:key="todo.id" :todo="todo">{{todo.name}}</TodoItem>
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem';
import uuid from 'uuid/v4';

export default {
  components: {
    TodoItem,
  },
  data() {
    return {
      todos: [],
      todoName: ''
    };
  },
  methods: {
    addTodo(name) {
      this.todos = [...this.todos, { id: uuid(), name }];
      return this.todos;
    },
  },
};
</script>


<style>
ul,
li {
  list-style: none;
  margin-left: 0;
  padding-left: 0;
}
</style>
