<template>
		<div class="view">
			<Toggle :id="id" :completed="completed" />
			<label @doubleClick="onDoubleClick">{{text}}</label>
			<Destroy :id="id" />
		</div>
</template>

<script>
import Toggle from './Toggle';
import Destroy from './Destroy';
export default {
  name: "View",
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
    }
  }
};
</script>
<style >
</style>