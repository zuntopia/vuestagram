<template>
    <div @click="filterClick" :class="`filter-item  ${filter}`" :style=" `background-image:url(${imgdataurl})`">
        <!-- <p>{{filter}}</p> -->
        <slot></slot>
    </div>
</template>

<script>
import EventBus from "./../EventBus.js"

export default {
    props: {
        imgdataurl: String,
        filter: String,
        },
    methods: {
        filterClick(){
            EventBus.$emit("selected_filter", this.filter);
        }
    }

}
</script>

<style>
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