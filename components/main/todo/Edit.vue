<template>
  <input class="edit" ref="inputEl" :value="editText" @change="onChange" @blur="onSubmit" @keydown="onKeyDown" />
</template>

<script>
export default {
  name: "Edit",
  components: {},
  props: {
    id: {
      type: Number,
      default: -1
    },
    text: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      editText:this.text
    };
  },
  computed: {},
  methods: {
    onChange({ target: { value } }){
      this.editText = value;
    },
    onSubmit({ target: { value: text } }) {
      if (text.trim() !== "") {
        this.$emit("edit", this.id, text);
      } else {
        this.$emit("destroy", this.id);
      }
    },
    onKeyDown(event) {
      const { keyCode } = event;

      if (keyCode === 13) {
        this.onSubmit(event);
      }

      if (keyCode === 27) {
        this.editText = text;
      }
    }
  }
};
</script>
<style >
</style>