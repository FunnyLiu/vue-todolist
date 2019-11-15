<template>
  <button class="clear-completed" :class="showClearCompletedClass" @click="onClick">Clear completed</button>
</template>


<script>
export default {
  name: "ClearCompleted",
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
      showClearCompletedClass() {
          return this.todos.filter(({ completed }) => completed).length !== 0 ? '' : 'hidden';
      }
  },
  methods: {
    onClick() {
        this.$emit('clear');
    }
  }
};
</script>
