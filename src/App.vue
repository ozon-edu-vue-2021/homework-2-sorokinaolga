<template>
  <div id="app">
    <all-component :items="items" />
  </div>
</template>

<script>
import data from '../public/static/node_modules.json';
import AllComponent from './components/AllComponent.vue';

export default {
  name: 'App',
  components: {
    AllComponent
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
