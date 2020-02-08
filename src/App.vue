<template>
  <div id="app">
<div class="header">
  <ul class="header-button-left">
    <li>Cancel</li>
  </ul>

  <ul class="header-button-right">
    <li>Next</li> 
  </ul>

  <img src="./assets/logo.png" class="logo">
</div>

<Body :posts="posts" :step="step" />

<div class="footer">
  <ul class="footer-button-plus">
    <li>+</li>
  </ul>
</div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Body from './components/Body.vue'
// import Post from './components/Post.vue'
import Postdata from './assets/postdata.js'

export default {
  data(){ 
    return {
      step: 2,
      posts: Postdata,
    }
  },
  name: 'App',
  components: {
    // HelloWorld
    Body,
    // Post,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
margin: 0;
}
ul{
padding: 5px;
list-style-type: none;
}
.logo {
width:22px;
margin: auto;
display: block;
position: absolute;
left: 0;
right: 0;
top: 13px;
}
.header {
width: 100%;
height: 40px;
background-color: white;
padding-bottom: 8px;
position: sticky;
top: 0;
}
.header-button-left {
color: skyblue;
float: left;
width: 50px;
padding-left: 20px;
cursor: pointer;
margin-top: 10px;
}
.header-button-right {
color: skyblue;
float: right;
width: 50px;
cursor: pointer;
margin-top: 10px;
}

body {
margin: 0;
}
ul{
padding: 5px;
list-style-type: none;
}
.logo {
width:22px;
margin: auto;
display: block;
position: absolute;
left: 0;
right: 0;
top: 13px;
}
.header {
width: 100%;
height: 40px;
background-color: white;
padding-bottom: 8px;
position: sticky;
top: 0;
}
.header-button-left {
color: skyblue;
float: left;
width: 50px;
padding-left: 20px;
cursor: pointer;
margin-top: 10px;
}
.header-button-right {
color: skyblue;
float: right;
width: 50px;
cursor: pointer;
margin-top: 10px;
}
</style>
