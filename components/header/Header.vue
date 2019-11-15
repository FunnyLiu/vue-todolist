<template>
    <header class="header">
        <h1>todos</h1>
        <Newtodo @add="add"/>
    </header>
</template>


<script>
import Newtodo from './NewTodo'
export default {
    name: 'Header',
    components:{
        Newtodo
    },
    methods:{
        add(text){
            this.$emit('add',text);
        }
    }
}
</script>
