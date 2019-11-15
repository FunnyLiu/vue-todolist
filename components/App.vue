<template>
  <div id="app">
    <Header @add="add" />
    <Main
      :todos="todos"
      :filter="filter"
      @toggle="onToggle"
      @destroy="onDestroy"
      @edit="onEdit"
      @toggleAll="onToggleAll"
    />
    <Footer :todos="todos" :filter="filter" @clear="onClear" />
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
      todos: [],
      filter: ""
    };
  },
  mounted() {
    window.addEventListener(
      "hashchange",
      event => {
        const newUrl = event.newURL;
        const curHash = newUrl.split("/")[4];
        switch (curHash) {
          case "":
            this.filter = "";
            break;
          case "active":
            this.filter = "active";
            break;
          case "completed":
            this.filter = "completed";
            break;
          default:
            this.filter = ""
            break;
        }
      },
      false
    );
  },
  methods: {
    add(text) {
      this.todos.push({
        text: text,
        completed: false,
        id: +new Date()
      });
    },
    onToggle(id) {
      this.todos.forEach(todo => {
        if (todo.id === id) {
          todo.completed = !todo.completed;
        }
      });
    },
    onDestroy(id) {
      this.todos = this.todos.filter(todo => {
        return todo.id !== id;
      });
    },
    onEdit(id, text) {
      this.todos.forEach(todo => {
        if (todo.id === id) {
          todo.text = text;
          todo.isEditing = !todo.isEditing;
        }
      });
    },
    onToggleAll(checked) {
      this.todos = this.todos.map(todo => ({ ...todo, completed: checked }));
    },
    onClear() {
      this.todos = this.todos.filter(({ completed }) => !completed);
    }
  }
};
</script>
