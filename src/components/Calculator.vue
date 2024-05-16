<template>
  <div class="calculator">
    <div class="header">
   
      <div class="input">
        <span>{{ current }}</span>
      </div>
    </div>
    <div class="keys">
      <div class="row">
        <div class="number">
          <span @click="clear">AC</span>
          <span @click="backspace">DEL</span>
          <span @click="append('%')">%</span>
        </div>
        <div class="symbol action" @click="append('/')">
          <span>/</span>
        </div>
      </div>
      <div class="row">
        <div class="number">
          <span @click="append('7')">7</span>
          <span @click="append('8')">8</span>
          <span @click="append('9')">9</span>
        </div>
        <div class="symbol action" @click="append('*')">
          <span>*</span>
        </div>
      </div>
      <div class="row">
        <div class="number">
          <span @click="append('4')">4</span>
          <span @click="append('5')">5</span>
          <span @click="append('6')">6</span>
        </div>
        <div class="symbol action" @click="append('-')">
          <span>-</span>
        </div>
      </div>
      <div class="row">
        <div class="number">
          <span @click="append('1')">1</span>
          <span @click="append('2')">2</span>
          <span @click="append('3')">3</span>
        </div>
        <div class="symbol action" @click="append('+')">
          <span>+</span>
        </div>
      </div>
      <div class="row">
        <div class="number">
          <span @click="append('0')">0</span>
          <span @click="append('.')">.</span>
        </div>
        <div class="symbol action" @click="calculate('=')">
          <span>=</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const current = ref("");

const append = (char) => {
  if (char === 'ac') {
    clear();
  } else if (char === 'del') {
    backspace();
  } else {
    current.value += char;
  }
};

const clear = () => {
  current.value = "";
};

const backspace = () => {
  current.value = current.value.slice(0, -1);
};

const calculate = () => {
  try {
    current.value = eval(current.value).toString();
  } catch (error) {
    current.value = "Error";
  }
};
</script>

<style scoped>
.calculator {
  width: 350px;
  height: 400px;
  border-radius: 10px;
  box-shadow: 0 25px 60px -10px rgba(0, 0, 0, 0.5);
  display: flex;
  flex-direction: column;
}

.header {
  background-color: #000;
  height: 120px;
  border-radius: 10px 10px 0 0;
  display: flex;
  flex-direction: column;
}

.window {
  height: 15px;
  display: flex;
  justify-content: flex-start;
  padding: 10px;
}

.window span {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  margin-right: 5px;
  cursor: pointer;
}

.input {
  color: #4a4a4a;
  text-align: right;
  padding: 10px 30px;
}

.input span {
  color: #ffffff;
}

.keys {
  background: linear-gradient(135deg, #3a3a3a, #000000);
  height: 350px;
  border-radius: 0 0 10px 10px;
  font-size: 24px;
  display: flex;
  flex-direction: column;
}

.row {
  height: 70px;
  display: flex;
  flex-direction: row;
}

.number {
  width: 75%;
  display: flex;
  color: #ffffff;
}

.number span {
  width: calc(100% / 3);
  height: 70px;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  user-select: none;
  cursor: pointer;
}

.symbol {
  width: 25%;
  background-color: #ffffff;
  font-size: 34px;
}

.symbol span {
  width: 100%;
  height: 70px;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  user-select: none;
  cursor: pointer;
}

.symbol.action {
  background: linear-gradient(60deg, #ff0300, #ffa100);
  border-radius: 0 0 10px 0;
  color: #ffffff;
  box-shadow: 0 25px 60px -10px rgba(255, 10, 0, 0.5);
}
</style>
