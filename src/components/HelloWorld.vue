<template>
  <div>

    <ul>
      <li v-for="todo in todos" v-bind:key="todo">{{ todo }}</li>
    </ul>

    <form v-on:submit.prevent="addTodo">
      <input v-model="todoText" placeholder="What needs to be done?">
      <button type="submit">Add Todo</button>
    </form>

  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data: function () {
    return {
      todos: [],
      todoText: '',
    };
  },
  methods: {
    addTodo: function () {
      this.todos = [...this.todos, this.todoText];
      localStorage.setItem('todos', JSON.stringify(this.todos));
    },
  },
  mounted: function () {
    const existingTodos = localStorage.getItem('todos');
    this.todos = JSON.parse(existingTodos) || [];
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
