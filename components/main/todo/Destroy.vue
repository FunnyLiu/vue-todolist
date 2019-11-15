<template>
  <button class="destroy" @click="onClick" />
</template>

<script>
export default {
  name: "Destroy",
  components: {},
  props: {
    id:{
      type:Number,
      default:-1
    }
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