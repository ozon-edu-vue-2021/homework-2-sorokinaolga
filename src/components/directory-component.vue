<template>
  <div>
    <FileComponent v-if="item.type==='file'" :item="item" />

    <LinkComponent v-if="item.type==='link'" :item="item" />

    <div :class="['item-directory__title', {'active': visible}]" v-if="item.type==='directory'" @click="visible=!visible">{{item.name}}</div>
    <ul class="item-directory__content" v-if="visible">
      <li v-for="itemList in item.contents" :key="itemList.name">
        <DirectoryComponent :item="itemList"/>
      </li>
    </ul>
  </div>
</template>

<script>
import FileComponent from './file-component.vue';
import LinkComponent from './link-component.vue';

export default {
  name: 'DirectoryComponent',
  props: ['item'],
  components: {
    FileComponent,
    LinkComponent,
  },
  data: function() {
    return {
      visible: false
    }
  },
}
</script>

<style scoped>
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
  width:600px;
}
</style>