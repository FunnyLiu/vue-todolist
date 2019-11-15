<template>
  <ul class="todo-list">
    <Todo
      v-for="(item, index) in visibleTodos"
      :key="item.id"
      :id="item.id"
      :text="item.text"
      :isEditing="item.isEditing"
      :setEditing="item.setEditing"
      :completed="item.completed"
    />
  </ul>
</template>

<script>
import Todo from './todo/Todo';
export default {
  name: "TodoList",
  components: {
    Todo
  },
  props: {
    todos: {
      type: Array,
      default: []
    },
    filter: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      editing: null
    };
  },
  computed: {
    visibleTodos() {
      debugger;
      let visibleTodos = [];
      if (this.filter === "active") {
        visibleTodos = this.todos.filter(
          ({ completed }) => completed === false
        );
      }

      if (this.filter === "completed") {
        visibleTodos = this.todos.filter(({ completed }) => completed);
      }
      visibleTodos = visibleTodos.map(todo => {
        todo.isEditing = todo.id === this.editing;
      });
      return visibleTodos;
    }
  },
  methods: {}
};
</script>
<style >
</style>