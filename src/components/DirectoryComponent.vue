<template>
  <div class="item-directory">
    <div class="item-directory__head" @click="toggleOpenItem">
      <div class="arrow_box" :class="{'arrow_box--open' : isOpen }"></div>
      <span class="item-directory__title">{{item.name}}</span>
    </div>
    <div v-show="isOpen" class="item-directory__content">
      <render-component :items="item.contents" />
    </div>
  </div>
</template>

<script>
import RenderComponent from './RenderComponent.vue';

export default {
  name: 'DirectoryComponent',
  components: {
    RenderComponent
  },
  props: ['item'],
  data: function() {
    return {
      isOpen: false
    }
  },
  methods: {
    toggleOpenItem() {
        this.isOpen = !this.isOpen
    },   
  }, 
}
</script>

<style scoped>
.item-directory__head {
  cursor:pointer;
  background-color: lightgreen;
  padding-left: 30px;
}
.item-directory__title {
  font: 22px/48px 'New Roman', serif;
}
.item-directory__content {
  overflow:hidden;
  width:600px;
}
.arrow_box {
  width:10px;
  height:10px;
  transition: all .3s;
  padding-bottom:0px;
  position:absolute;
  margin:20px 0px 0px -15px;
  
}
.arrow_box:after, .arrow_box:before {
	border: solid transparent;
	content: " ";
	position: absolute;
}
.arrow_box:after {
	border-width: 5px;
}
.arrow_box:before {
	border-left-color: #000;
	border-width: 5px;
}
.arrow_box--open{
   transform: rotateZ(90deg);
   transform-origin: 50% 50%;
}
</style>
