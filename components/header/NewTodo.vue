<template>
  <div>
    <input
      class="new-todo"
      placeholder="What needs to be done?"
      v-model="text"
      @keydown="onKeyDown"
      autofocus
    />
  </div>
</template>


<script>
export default {
  name: "Newtodo",
  data() {
    return {
      text: ""
    };
  },
  methods: {
    onKeyDown(event) {
      const { keyCode } = event;
      if (keyCode !== 13) {
        return;
      }
      event.preventDefault();
      const newText = this.text.trim();

      if (newText !== "") {
        this.$emit("add", newText);
        this.text = "";
      }
    }
  }
};
</script>
