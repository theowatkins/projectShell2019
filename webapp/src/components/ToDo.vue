<template>
  <div class="todo columns">
    <b-checkbox v-model="todo.done" v-on:input="handleCheck" />
    <span class="todo-title column">
      {{ todo.title }} - category: {{todo.category}}
    </span>
    <b-button v-on:click="handleDelete">Delete</b-button>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  props: {
    todo: {
      type: Object,
      default: () => {
        return {};
      }
    }
  },
  methods: {
    handleCheck: function(value) {
      this.$store.dispatch("loadToDos");
      console.log(this.todo.id);
      this.$store.dispatch("updateTodo", { ...this.todo, done: value });
    },
    handleDelete: function() {
      this.$store.dispatch("loadToDos");
      console.log(this.todo.id);
      this.$store.dispatch("deleteTodo", this.todo);
    }
  }
};
</script>
