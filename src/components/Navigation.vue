<template>
  <nav class="navbar navbar-light bg-light">
    <a class="navbar-brand">{{title}}</a>
    <form class="form-inline" v-if="searchbar">
      <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search" disabled>
      <button class="btn btn-outline-success my-2 my-sm-0" type="submit" disabled>Search</button>
    </form>

    <button class="btn btn-outline-secondary" v-if="toggleable" @click="toggleDrawer">
      Toggle Drawer
    </button>

    <button class="btn btn-outline-secondary" v-if="add" @click="addList">
      + Add List
    </button>

  </nav>
</template>
<script>
export default {
  name: 'Navigation',
  props: [
      'title',
      'searchbar',
      'add',
      'toggleable'
  ],
  methods: {
    addList: function () {
      this.$store.dispatch('addList', {
        id: this.$store.state.lists.length + 1,
        name: 'New List',
        tasks: [],
      });
    },
    toggleDrawer: function () {
      this.$store.state.drawerOpen = !this.$store.state.drawerOpen;
    }
  }
}
</script>
