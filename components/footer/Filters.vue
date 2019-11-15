<template>
  <ul class="filters">
    <li>
      <a :class="selectedClass('')" href="#/" > All </a>
    </li>
    <li>
      <a :class="selectedClass('active')" href="#/active" > Active </a>
    </li>
    <li>
      <a :class="selectedClass('completed')" href="#/completed" > Completed </a>
    </li>
  </ul>
</template>


<script>
export default {
  name: "Filters",
  components: {},
  props: {
    filter: {
      type: String,
      default: ""
    }
  },
  methods: {
    selectedClass(match) {
      return this.filter === match ? "selected" : "";
    }
  }
};
</script>
