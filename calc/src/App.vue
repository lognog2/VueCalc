<script setup>
import { ref, createApp, onErrorCaptured} from 'vue'
//import App from './App.vue'
//const app = createApp(App)

//expression string that appears on top bar
const exp = ref('')

//boolean for whether expression is in editable state.
//if user tries to add a value when false, bar will clear
const editable = ref(false)

//resets expression
function reset() {
  exp.value = ('')
  editable.value = true
}

//adds a character to the expression
function add(x) {
  if (editable.value == false) {
    reset()
  }
  exp.value = exp.value.concat(exp.value, x)
}

//computes expression
//handles errors that occur (including division by 0)
function compute() {
  try {
    exp.value = eval(exp.value).toString()
    if (exp.value == 'Infinity') {
      throw new Error('Division by zero')
    }
  } catch (err) {
    alert('Error: ' + err)
    exp.value = 'Error'
    editable.value = false
  }

}

</script>

<template>
  <h1>
    Calculator
  </h1>
  <div>
    <input v-model="exp">
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

