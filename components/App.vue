<template>
  <div id="app">
    <Header @add="add" />
    <Main :todos="todos" />
    <Footer />
  </div>
</template>


<script>
import Header from "./header/Header";
import Main from "./main/Main";
import Footer from "./footer/Footer";
export default {
  components: {
    Header,
    Main,
    Footer
  },
  data: () => {
    return {
      todos: []
    };
  },
  methods: {
    add(text) {
      this.todos.push({
        text: text,
        completed: false,
        id: +new Date()
      });
    }
  }
};
</script>
