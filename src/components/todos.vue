<template>
  <div>
    <TodoItem
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:todo="todo"
      @deleteTodo="$emit('deleteTodo', todo.id)"
    />
  </div>
</template>

<script>
import TodoItem from './todoItem';
export default {
  name: 'Todos',
  components: {
    TodoItem
  },
  props: {
    todos: {
      type: Array
    }
  },
  methods: {}
};
</script>

<style></style>
