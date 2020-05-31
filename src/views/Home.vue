<template>
  <div id="app">
    <div class="container">
      <!-- <myHeader /> -->
      <AddTodo @addNewTodo="addTodo" />
      <Todos v-bind:todos="todos" @deleteTodo="deleteTodo" />
    </div>
  </div>
</template>

<script>
// import myHeader from './components/myHeader';
import AddTodo from '../components/addTodo';
import Todos from '../components/todos';
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    // myHeader,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    addTodo(Newtitle) {
      axios
        .post('https://jsonplaceholder.typicode.com/todos', {
          title: Newtitle,
          completed: false
        })
        .then(res => {
          this.todos.push(res.data);
        });
    },

    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  },
  created() {
    axios
      .get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => {
        this.todos = res.data;
      })
      .catch(err => console.log(err));
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
