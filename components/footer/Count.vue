<template>
  <span class="todo-count">
    <strong>{{activeCount}}</strong>
    {{itemsLeft}}
  </span>
</template>


<script>
export default {
  name: "Count",
  components: {},
  props: {
    todos: {
      type: Array,
      default: () => {
        return [];
      }
    }
  },
  computed: {
    activeCount() {
      const activeCount = this.todos.filter(({ completed }) => completed === false).length;
      return activeCount;
    },
    itemsLeft() {
        return ` item${this.activeCount !== 1 ? 's' : ''} left`;
    }
  }
};
</script>
