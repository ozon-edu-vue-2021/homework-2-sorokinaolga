<template>
  <ul>
    <li 
      v-for="item in items"
      :key="item"
    >

    <div class="item-file" v-if="item.type==='file'">
      <span>{{item.name}}</span>
    </div>

    <div class="item-link" v-if="item.type==='link'">
      <span>{{item.name}}</span>
    </div>

    <directory-component v-if="item.type==='directory'" :item="item" />

    </li>
  </ul>
</template>

<script>
import DirectoryComponent from './DirectoryComponent.vue';

export default {
  name: 'RenderComponent',
  components: {
    DirectoryComponent
  },
  props: ['items']
}
</script>

<style scoped>
li {
  list-style:none;
}
.item-file,
.item-link {
  font: 14px/22px 'New Roman', serif;
  padding-bottom:20px;
}
</style>
