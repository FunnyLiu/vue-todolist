<template>
  <li 
  :class="editingClass" 
  >
    <View :id="id" :completed="completed" :text="text" @setEditing="setEditing" />
    <Edit :id="id" :completed="completed" :text="text" @setEditing="setEditing" />
  </li>
</template>

<script>
export default {
  name: "Todo",
  components: {},
  props: {
    id:{
      type:Number,
      default:-1
    },
    completed:{
      type:Boolean,
      default:false
    },
    isEditing: {
      type:Boolean,
      default:false
    },
    text:{
      type:String,
      default:''
    }
  },
  data() {
    return {};
  },
  computed: {
    editingClass(){
      return this.isEditing ? "editing" : "";
    },
    completedClass() {
      return this.completed ? "completed" : ""
    }
  },
  methods: {
    setEditing(id){
      console.warn(`setEditing ${id}`);
    }
  }
};
</script>
<style >
</style>