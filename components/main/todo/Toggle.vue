<template>
  <input class="toggle" type="checkbox" :checked="completed" @change="onChange" />
</template>

<script>
export default {
  name: "Toggle",
  components: {},
  props: {
    id: {
      type: Number,
      default: -1
    },
    completed: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {};
  },
  computed: {},
  methods: {
    onChange() {
      this.$emit("toggle", this.id);
    }
  }
};
</script>
<style >
</style>