<template>
  <form @submit.prevent="onSubmit">
    <input
      v-model="title"
      type="text"
      name="title"
      placeholder="Add Todo ..."
      class="input-one"
    />
    <input type="submit" class="btn btn-input" />
  </form>
</template>

<script scoped>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    };
  },
  methods: {
    onSubmit() {
      this.$emit('addNewTodo', this.title);
      this.title = '';
    }
  }
};
</script>

<style>
form {
  display: flex;
}
.btn-input {
  flex: 1;
}
.input-one {
  flex: 10;
  padding: 5px;
}
</style>
