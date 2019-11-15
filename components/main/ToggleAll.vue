<template>
  <div class="ToggleAll">
    <input
      id="toggle-all"
      class="toggle-all"
      type="checkbox"
      :checked="isToggled"
      @change="onChange"
    />
    <label for="toggle-all">Mark all as complete</label>
  </div>
</template>

<script>
export default {
  name: "ToggleAll",
  components: {},
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
    isToggled() {
      return this.todos.every(({ completed }) => completed);
    }
  },
  methods: {
    onChange({ target: { checked } }) {
      this.$emit({ type: "toggle-all", checked });
    }
  }
};
</script>
<style >
</style>