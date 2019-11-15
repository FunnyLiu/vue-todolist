<template>
  <button class="destroy" @click={onClick} />
</template>

<script>
export default {
  name: "Destroy",
  components: {},
  props: {
    id
  },
  data() {
    return {};
  },
  computed: {},
  methods: {
    onClick() {
      this.$emit('destroy',this.id)
    }
  }
};
</script>
<style >
</style>