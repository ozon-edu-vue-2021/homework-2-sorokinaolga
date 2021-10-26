<template>
  <div id="app">
    <directory-component :items="items" />
  </div>
</template>

<script>
import data from '../public/static/node_modules.json';
import DirectoryComponent from './components/DirectoryComponent.vue';

export default {
  name: 'App',
  components: {
    DirectoryComponent
  },
  data() { return {
    items: [data]
  }}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
