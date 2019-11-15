<template>
  <footer class="footer" :class="noTodosClass">
    <Count />
    <Filters />
    <ClearCompleted />
  </footer>
</template>


<script>
import ClearCompleted from './ClearCompleted'
import Count from './Count';
import Filters from "./Filters";
export default {
  name: "Footer",
  components: {
    ClearCompleted,
    Count,
    Filters
  },
  props: {
    todos: {
      type: Array,
      default: () => {
        return [];
      }
    }
  },
  computed: {
    noTodosClass() {
      const noTodosClass = this.todos.length === 0 ? "hidden" : "";
      return noTodosClass;
    }
  }
};
</script>
