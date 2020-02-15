<template>
  <div id="app">
<div class="header">
  <ul class="header-button-left" v-if="step == 1">
    <li>Cancel</li>
  </ul>

  <ul class="header-button-right" v-on:click="step=2" v-if="step == 1">
    <li>Next</li> 
  </ul>

  <ul class="header-button-right" v-on:click="publish" v-if="step == 2">
    <li>Publish</li> 
  </ul>

  <img src="./assets/logo.png" class="logo">
</div>

<Body :filters="filters" :posts="posts" :step="step" :imgdataurl="imgdataurl" v-on:content='content=$event'/>

<div class="footer">
  <ul class="footer-button-plus">
    <input v-on:change="upload" type="file" id="file" class="inputfile" >
    <label for="file" class="input-plus">+</label>
  </ul>
</div>
  </div>
</template>

<script>
import Body from './components/Body.vue'
import Postdata from './assets/postdata.js'

export default {
  data(){ 
    return {
      step: 0,
      posts: Postdata,
      imgdataurl: "",
      content: "",
      filters: [ "normal", "clarendon", "gingham", "moon", "lark", "reyes", "juno", "slumber", "aden", "perpetua", "mayfair", "rise", "hudson", "valencia", "xpro2", "willow", "lofi", "inkwell", "nashville"],
    
    }
  },
  name: 'App',
  components: {
    // HelloWorld
    Body,
    // Post,
  },
  methods: {
     upload(e){
      this.step = 1;
      let file = e.target.files;
      let reader = new FileReader();
      reader.readAsDataURL(file[0]);
      // this.imgdataurl = e.target.result;
      reader.onload = e => {
        this.imgdataurl = e.target.result;
        console.log(e.target.result)
      }
    },
    publish(){

      let newitem = {
        name: "HJWORKS",
        userImage: "https://placeimg.com/200/200/arch",
        postImage: this.imgdataurl,
        likes: 20,
        date: 'Apr 20',
        liked: false,
        caption: this.content,
        filter: "clarendon"
      }
      this.posts.unshift(newitem);
      this.step=0;
    }
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
