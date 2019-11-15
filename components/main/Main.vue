<template>
  <section class="main" :class="noTodosClass">
    <ToggleAll :todos="todos" @toggleAll="onToggleAll" />
    <TodoList :todos="todos" :filter="filter" @toggle="onToggle" @destroy="onDestroy" @edit="onEdit"/> 
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
    },
    filter: {
      type: String,
      default: ''
    }
  },
  data() {
    return {};
  },
  computed: {
    noTodosClass() {
      return this.todos.length === 0 ? "hidden" : "";
    }
  },
  methods: {
    onToggle(id){
      this.$emit('toggle',id);
    },
    onDestroy(id){
      this.$emit('destroy',id);
    },
    onEdit(id,text){
      this.$emit('edit',id,text);
    },
    onToggleAll(checked){
      this.$emit('toggleAll',checked);
    }
  }
};
</script>
<style >
</style>