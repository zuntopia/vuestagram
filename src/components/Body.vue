<template>
<div class="body">
  <!-- <Post v-for:"item in Data" key:/> -->
  <!-- <Post /> -->
  <Post v-for="post in posts" :key="post" :post="post"/>
  <!-- <Post /> -->
</div>
</template>

<script>
// import Data from '../assets/postdata.js'
import Post from './Post.vue'

export default {
    name: 'body',
    components: {
        Post,
    },
    props: {
        posts: Array,
        }
        
}
</script>

<style>

</style>