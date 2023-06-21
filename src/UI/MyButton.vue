<template>
    <button ><slot></slot></button>
</template>

<script>
export default {
    name: 'MyButton'
}</script>

<style scoped>
button {
    height:100px;
    width:100px;
    border-radius:50%;
    border:2px solid teal;
    background:none;
    color:teal;
    font-size:24pt;
    font-family: 'Montserrat', sans-serif;
    margin-top:10px;
    margin-right:5px;
    margin-left:5px;
}
</style>