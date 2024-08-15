<script setup>
import { ref, createApp, onErrorCaptured} from 'vue'
//import App from './App.vue'
//const app = createApp(App)

//string
const op = ref('')
//array of each individual character
const exp = ref([''])

//resets expression
function reset() {
  op.value = ('')
}

//adds a character to the expression
function add(x) {
  exp.value = op.value.split('')
  exp.value.push(x)
  op.value = exp.value.join('')
}

//computes expression
function compute() {
  op.value = eval(op.value).toString()
  if (op.value == 'Infinity')
    op.value = 'Error: Divide by zero'
}
</script>

<template>
  <h1>
    Calculator
  </h1>
  <div>
    <input v-model="op">
  </div>
  <div>
    <button @click="add('+')">+</button>
    <button @click="add('-')">-</button>
    <button @click="add('/')">/</button>
    <button @click="add('*')">*</button>
  </div>
  <div>
    <button @click="add('1')">1</button>
    <button @click="add('2')">2</button>
    <button @click="add('3')">3</button>
  </div>
  <div>
    <button @click="add('4')">4</button>
    <button @click="add('5')">5</button>
    <button @click="add('6')">6</button>
  </div>
  <div>
    <button @click="add('7')">7</button>
    <button @click="add('8')">8</button>
    <button @click="add('9')">9</button>
  </div>
  <div>
    <button @click="reset">C</button>
    <button @click="add('0')">0</button>
    <button @click="compute">=</button>
  </div>
</template>

