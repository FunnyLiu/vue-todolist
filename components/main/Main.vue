<template>
  <section class="main" :class="noTodosClass">
    <ToggleAll />
    <TodoList :todos="todos" /> 
  </section>
</template>

<script>
import ToggleAll from './ToggleAll';
import TodoList from './TodoList';

export default {
  name: "Main",
  components: {
    ToggleAll,
    TodoList
  },
  props: {
    todos: {
      type: Array,
      default: () => {
        return [];
      }
    }
  },
  data() {
    return {};
  },
  computed: {
    noTodosClass() {
      debugger;
      return this.todos.length === 0 ? "hidden" : "";
    }
  },
  methods: {}
};
</script>
<style >
</style>