<template>
<div class="body">
  <div v-if="step == 0">
  <Post v-for="(post, i) in posts" :key="i" :post="posts[i]"/>
  </div>

  <div v-if="step == 1"> 
    <div :class="`upload-image ${clicked_filter}`" :style=" `background-image:url(${imgdataurl})`"></div>
    <div class="filters">
      <FilterBox 
        v-for="filter in filters" 
        :key="filter" 
        :filter="filter" 
        :imgdataurl="imgdataurl" 
        v-on:clicked_filter='clicked_filter=clicked_filter'>
        <p>{{filter}}</p>
      </FilterBox>
    </div>
  </div>

  <div v-if="step == 2"> 
    <div :class="`upload-image ${clicked_filter}`" :style=" `background-image:url(${imgdataurl})`"></div>
    <textarea v-on:input="$emit('content', $event.target.value)" class="write-box">write!</textarea>
  </div>
  <!-- <button v-on:click="$emit('send', 'sendsendsnedsendnsend')">button</button> -->
</div>
</template>

<script>
import Post from './Post.vue'
import FilterBox from './FiltorBox.vue'
import EventBus from './../EventBus.js'

export default {
  data(){ 
    return {
      clicked_filter: "",
      }
    },
  mounted(){
    EventBus.$on('selected_filter', (myEvent) => {
      /* eslint-disable */
      this.clicked_filter=myEvent;
    })
  },
    name: 'body',
    components: {
        Post,
        FilterBox,
    },
    props: {
        step: Number,
        posts: Array,
        imgdataurl: String,
        filters: Array,
        }
}
</script>

<style>
.upload-image{
width: 100%;
height: 450px;
background: cornflowerblue;
background-size : cover;
}
.filters{
overflow-x:scroll;
white-space: nowrap;
}
.filter-1 {
width: 100px;
height: 100px;
background-color: cornflowerblue;
margin: 10px 10px 10px auto;
padding: 8px;
display: inline-block;
color : white;
background-size: cover;
}
.filters::-webkit-scrollbar {
height: 5px;
}
.filters::-webkit-scrollbar-track {
background: #f1f1f1; 
}
.filters::-webkit-scrollbar-thumb {
background: #888; 
border-radius: 5px;
}
.filters::-webkit-scrollbar-thumb:hover {
background: #555; 
}
.write-box {
border: none;
width: 90%;
height: 100px;
padding: 15px;
margin: auto;
display: block;
outline: none;
}
.filter-item {
width: 100px;
height: 100px;
margin: 10px 10px 10px auto;
padding: 8px;
display: inline-block;
color : white;
background-size: cover;
background-position : center;
}
</style>