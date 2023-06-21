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
}
</style>