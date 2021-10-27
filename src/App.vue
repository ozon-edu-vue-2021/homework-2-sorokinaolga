<template>
  <div id="app">
    <ul>
      <li 
        v-for="item in items"
        :key="item.name"
      >
        <DirectoryComponent :item="item" />
      </li>
    </ul>
  </div>
</template>

<script>
import data from '../public/static/node_modules.json';
import DirectoryComponent from './components/directory-component.vue';

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
li {
  list-style:none;
}
</style>
