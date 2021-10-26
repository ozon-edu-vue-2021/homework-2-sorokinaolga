<template>
  <ul>
    <li 
      v-for="(item, index) in items"
      :key="`${item}-${index}`"
    >

    <file-component v-if="item.type==='file'" :item="item" />

    <link-component v-if="item.type==='link'" :item="item" />

    <div class="item-directory" v-if="item.type==='directory'">
        <div class="item-directory__title" @click="toggleItemActive">
          {{item.name}}
        </div>
        <div class="item-directory__content">
            <directory-component :items="item.contents" />
        </div>
    </div>

    </li>
  </ul>
</template>

<script>
import FileComponent from './FileComponent.vue';
import LinkComponent from './LinkComponent.vue';

export default {
  name: 'DirectoryComponent',
  props: ['items'],
  components: {
    FileComponent,
    LinkComponent,
  },
  methods: {
    toggleItemActive: function(evt) {
      evt.target.classList.toggle('active');
    },   
  }, 
}
</script>

<style scoped>
li {
  list-style:none;
}
.item-directory__title {
  position: relative;
  font: 22px/48px 'New Roman', serif;
  cursor:pointer;
  background-color: #8dec8d;
  padding-left: 40px;
  border-radius: 8px;
  border: 1px solid #038d03;
  margin-bottom: 2px;
  margin-right: 30px;
}
.item-directory__title:hover {
  background-color: #67ce67;
}
.item-directory__title::before {
  content: '>';
  display: block;
  position: absolute;
  left: 15px;
}
.item-directory__title.active::before {
  content: 'x';
}
.item-directory__content {
  display: none;
  width:600px;
}
.item-directory__title.active + .item-directory__content {
  display: block;
}
</style>