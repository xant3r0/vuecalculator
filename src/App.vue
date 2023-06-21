<template>
  <div class="app">
    <div id="calculator">
      <h1>{{ this.display }}</h1>
      <div class="btns">
        <MyButton @click="addOnDisplay">1</MyButton>
        <MyButton>2</MyButton>
        <MyButton>3</MyButton>
        <MyButton @click="addNumbers">+</MyButton>
        <MyButton>4</MyButton>
        <MyButton>5</MyButton>
        <MyButton>6</MyButton>
        <MyButton>-</MyButton>
        <MyButton>7</MyButton>
        <MyButton>8</MyButton>
        <MyButton>9</MyButton>
        <MyButton @click="Equal">=</MyButton>
        <MyButton style="width: 300px;border-radius:20%">0</MyButton>
        <MyButton @click="deleteFromScreen">AC</MyButton>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
    display:'',
    secondValue:"",
    v1:"",
    v2:""
    }
  },
  methods: {
    addOnDisplay(event) {
      event.preventDefault();
      this.display = this.display + 1;
    },
    deleteFromScreen(event) {
      event.preventDefault();
      this.display = '';
    },
    addNumbers(event) {
      event.preventDefault();
      this.secondValue = this.display;
      this.display = '';
    },
    Equal(event) {
      event.preventDefault();
      this.v1 = parseInt(this.display);
      this.v2 = parseInt(this.secondValue);
      this.display = this.v1 + this.v2;
    }
  }
}
</script>

<style>
* {
  margin:0;
  padding:0;
  box-sizing: border-box;
}
.app {
  width:100%;
  height:100vh;
  display:flex;
  justify-content: center;
  align-items: center;
}
.display {
  height:100px;
  width: 100%;
  border:2px solid teal;
  border-radius:3%;
  color:teal;
}
.btns {
  max-width: 400px;
}
h1 {
  color:teal;
  font-size:24pt;
}
</style>
