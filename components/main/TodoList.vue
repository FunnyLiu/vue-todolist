<template>
  <ul class="todo-list">
    <Todo
      v-for="(item, index) in visibleTodos"
      :key="item.id"
      :id="item.id"
      :text="item.text"
      :isEditing="item.isEditing"
      @setEditing="setEditing"
      :completed="item.completed"
      @toggle="onToggle"
      @destroy="onDestroy"
      @edit="onEdit"
    />
  </ul>
</template>

<script>
import Todo from "./todo/Todo";
export default {
  name: "TodoList",
  components: {
    Todo
  },
  props: {
    todos: {
      type: Array,
      default: () => {
        return [];
      }
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
      let visibleTodos = this.todos;
      if (this.filter === "active") {
        visibleTodos = this.todos.filter(
          ({ completed }) => completed === false
        );
      }

      if (this.filter === "completed") {
        visibleTodos = this.todos.filter(({ completed }) => completed);
      }
      visibleTodos.forEach(todo => {
        if(todo.id === this.isEditing){
          todo.isEditing = true;
        }else{
          todo.isEditing = false;
        }
        todo.isEditing = todo.id === this.editing;
      });
      return visibleTodos;
    }
  },
  methods: {
    onToggle(id){
      this.editing = null;
      this.$emit('toggle',id);
    },
    onDestroy(id){
      this.$emit('destroy',id);
    },
    setEditing(id){
      this.editing = id;
    },
    onEdit(id,text){
      this.$emit('edit',id,text);
    }
  }
};
</script>
<style >
</style>