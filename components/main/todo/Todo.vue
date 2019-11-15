<template>
  <li :class="[editingClass,completedClass]">
    <Viewer :id="id" :completed="completed" :text="text" @setEditing="setEditing" @toggle="onToggle" @destroy="onDestroy" />
    <Edit :id="id" :completed="completed" :text="text" @setEditing="setEditing" @edit="onEdit" />
  </li>
</template>

<script>
import Viewer from "./View";
import Edit from "./Edit";

export default {
  name: "Todo",
  components: {
    Viewer,
    Edit
  },
  props: {
    id: {
      type: Number,
      default: -1
    },
    completed: {
      type: Boolean,
      default: false
    },
    isEditing: {
      type: Boolean,
      default: false
    },
    text: {
      type: String,
      default: ""
    }
  },
  data() {
    return {};
  },
  computed: {
    editingClass() {
      return this.isEditing ? "editing" : "";
    },
    completedClass() {
      return this.completed ? "completed" : "";
    }
  },
  methods: {
    setEditing(id) {
      this.$emit('setEditing',id)
    },
    onToggle(id){
      this.$emit('toggle',id);
    },
    onDestroy(id){
      this.$emit('destroy',id);
    },
    onEdit(id,text){
      this.$emit('edit',id,text);
    }
  }
};
</script>
<style >
</style>