<template>
		<div class="view">
			<Toggle :id="id" :completed="completed" @toggle="onToggle" />
			<label v-on:dblclick="onDoubleClick">{{text}}</label>
			<Destroy :id="id" @destroy="onDestroy" />
		</div>
</template>

<script>
import Toggle from './Toggle';
import Destroy from './Destroy';
export default {
  name: "Viewer",
  components: {
    Toggle,
    Destroy
  },
  props: {
    id:{
      type:Number,
      default:-1,
    },
    text:{
      type:String,
      defalut:''
    },
    completed:{
      type:Boolean,
      defalut:false
    }
  },
  data() {
    return {};
  },
  computed: {},
  methods: {
    onDoubleClick() {
      this.$emit('setEditing',this.id)
    },
    onToggle(id) {
      this.$emit('toggle',id);
    },
    onDestroy(id) {
      this.$emit('destroy',id);
    }
  }
};
</script>
<style >
</style>