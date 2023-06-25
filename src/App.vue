<template>
  <div class="app">
    <div id="calculator">
      <h1>{{ this.display }}</h1>
      <div class="btns">
        <MyButton @click="deleteFromScreen">AC</MyButton>
        <MyButton @click="plusMinus">+/-</MyButton>
        <MyButton @click="addComma">,</MyButton>
        <MyButton @click="divNumbers">/</MyButton>
        <MyButton @click="addOnDisplay7">7</MyButton>
        <MyButton @click="addOnDisplay8">8</MyButton>
        <MyButton @click="addOnDisplay9">9</MyButton>
        <MyButton @click="addNumbers">+</MyButton>
        <MyButton @click="addOnDisplay4">4</MyButton>
        <MyButton @click="addOnDisplay5">5</MyButton>
        <MyButton @click="addOnDisplay6">6</MyButton>
        <MyButton @click="downNumbers">-</MyButton>
        <MyButton @click="addOnDisplay1">1</MyButton>
        <MyButton @click="addOnDisplay2">2</MyButton>
        <MyButton @click="addOnDisplay3">3</MyButton>
        <MyButton @click="multNumbers">x</MyButton>
        <MyButton @click="addOnDisplay0" style="width: 320px;border-radius:45px;">0</MyButton>
        <MyButton @click="Equal">=</MyButton>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numArr:[],
      operators:[],
      display:"0",
      afterEqual:false
    }
  },
  methods: {
    deleteFromScreen(event) {
      event.preventDefault();
      this.display = "0";
      this.numArr = [];
      this.operators = [];
    },
    plusMinus(event) {
      event.preventDefault();
      this.display = parseFloat(this.display) * -1;
    },
    addComma(event) {
      event.preventDefault();
      
      let isTrue = true;

      for(let i = 0;i <= this.display.length - 1;i++) {
        if(this.display[i] === '.') {
          isTrue = false;
          break;
        } 
      };

      if(isTrue === true) {
        this.display = this.display + '.';
      };
    },
    divNumbers(event) {
      event.preventDefault();
      this.numArr.push(this.display);
      this.operators.push("/");
      this.display = "0";
    },
    addOnDisplay1(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 1;
      } else {
        this.display = "1";
        this.afterEqual = false;
      }
    },
    addOnDisplay2(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 2;
      } else {
        this.display = "2";
        this.afterEqual = false;
      }
    },
    addOnDisplay3(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 3;
      } else {
        this.display = "3";
        this.afterEqual = false;
      }
    },
    addOnDisplay4(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 4;
      } else {
        this.display = "4";
        this.afterEqual = false;
      }
    },
    addOnDisplay5(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 5;
      } else {
        this.display = "5";
        this.afterEqual = false;
      }
    },
    addOnDisplay6(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 6;
      } else {
        this.display = "6";
        this.afterEqual = false;
      }
    },
    addOnDisplay7(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 7;
      } else {
        this.display = "7";
        this.afterEqual = false;
      }
    },
    addOnDisplay8(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 8;
      } else {
        this.display = "8";
        this.afterEqual = false;
      }
    },
    addOnDisplay9(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 9
      } else {
        this.display = "9";
        this.afterEqual = false;
      }
    },
    addOnDisplay0(event) {
      event.preventDefault();
      if(this.display !== "0" && this.afterEqual !== true) {
        this.display = this.display + 0;
      } else {
        this.display = "0";
        this.afterEqual = false;
      }
    },
    addNumbers(event) {
      event.preventDefault();
      this.numArr.push(this.display);
      this.operators.push("+");
      this.display = "0";
    },
    downNumbers(event) {
      event.preventDefault();
      this.numArr.push(this.display);
      this.operators.push("-");
      this.display = "0";
    },
    multNumbers(event) {
      event.preventDefault();
      this.numArr.push(this.display);
      this.operators.push("*");
      this.display = "0";
    },
    Equal(event) {
      event.preventDefault();
      let result = parseInt(this.numArr[0]);
      this.numArr.push(this.display);

      for(let i = 0;i <= this.operators.length - 1;i++) {
        switch(this.operators[i]) {
          case '+':
            result = result + parseInt(this.numArr[i + 1]);
            break;
          case '-':
            result = result - parseFloat(this.numArr[i + 1]);
            break;
          case '*':
            result = result * parseFloat(this.numArr[i + 1]);
            break;
          case '/':
            result = result / parseFloat(this.numArr[i + 1]);
            break;
        };
      };
      this.display = result;
      this.afterEqual = true;
    }
  }
}
</script>

<style>
* {
  margin:0;
  padding:0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
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
  max-width: 440px;
}
h1 {
  color:teal;
  font-size:72px;
  text-align:end;
}
#calculator {
  border:2px solid teal;
  padding-top:100px;
  padding-bottom: 30px;
  padding-left: 30px;
  padding-right:30px;
  border-radius: 45px;
}
</style>
