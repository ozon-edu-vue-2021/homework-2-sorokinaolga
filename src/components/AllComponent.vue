<template>
  <ul>
    <li 
      v-for="(item, index) in items"
      :key="`${item}-${index}`"
    >

    <div class="item-file" v-if="item.type==='file'">
      <span>{{item.name}}</span>
    </div>

    <div class="item-link" v-if="item.type==='link'">
      <span>{{item.name}}</span>
    </div>

    <div class="item-directory" v-if="item.type==='directory'">
        <div class="item-directory__head" @click="toggleOpenItem">
        <div class="arrow_box" :class="{'arrow_box--open' : isOpen }"></div>
            <span class="item-directory__title">{{item.name}}</span>
        </div>
        <div v-show="isOpen" class="item-directory__content">
            <all-component :items="item.contents" />
        </div>
    </div>

    </li>
  </ul>
</template>

<script>

export default {
  name: 'AllComponent',
  props: ['items'],
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
li {
  list-style:none;
}
.item-file,
.item-link {
  font: 14px/22px 'New Roman', serif;
  padding-bottom:20px;
}
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