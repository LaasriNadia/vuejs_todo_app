<template>
  <div id="app">
    <div class="container">
      <AddTodo @addNewTodo="addTodo" />
      <Todos v-bind:todos="todos" @deleteTodo="deleteTodo" />
    </div>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

import AddTodo from '../components/addTodo';
import Todos from '../components/todos';
export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          title: 'lorem remaining essentially unchange',
          completed: false,
          id: 1
        },
        { title: 'remaining lorem unchange', completed: true, id: 2 },
        {
          title: 'remazeing essly lorem',
          completed: false,
          id: 3
        }
      ]
    };
  },
  methods: {
    addTodo(Newtitle) {
      this.todos.push({
        id: uuidv4(),
        title: Newtitle,
        completed: false
      });
    },

    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, serif;
  line-height: 1.4;
}

a {
  color: #333;
  text-decoration: none;
}

.container {
  padding: 0 1rem;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
