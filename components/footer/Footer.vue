<template>
  <footer class="footer" :class="noTodosClass">
    <Count :todos="todos" />
    <Filters :filter="shadowFilter" />
    <ClearCompleted :todos="todos" @clear="onClear" />
  </footer>
</template>


<script>
import ClearCompleted from "./ClearCompleted";
import Count from "./Count";
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
    },
    filter: {
      type: String,
      default: ""
    }
  },
  computed: {
    shadowFilter() {
      return this.filter;
    },
    noTodosClass() {
      const noTodosClass = this.todos.length === 0 ? "hidden" : "";
      return noTodosClass;
    }
  },
  methods: {
    onClear() {
      this.$emit("clear");
    }
  }
};
</script>
