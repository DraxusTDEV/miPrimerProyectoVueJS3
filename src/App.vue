<script setup>
import {ref, computed} from 'vue'

const counter = ref(0);
const disabled = true;

const arrayFavoritos = ref([]);

const increment = () =>{
  counter.value++;
  console.log(counter.value);
}

const decrement = () =>{
  counter.value--;
  console.log(counter.value);
}

const reset = () =>{
  counter.value = 0;
  console.log(counter.value);
}

const add = () => {
  arrayFavoritos.value.push(counter.value)
  console.log(arrayFavoritos.value);
}

const classCounter = computed(() => {
  if(counter.value > 0){
    return 'positive';
  }
  if(counter.value < 0){
    return 'negative';
  }
  if(counter.value === 0){
    return 'zero';
  }
})


const blockBtnAdd = computed(() => {
  const numSearch = arrayFavoritos.value.find((num) => num === counter.value);
  console.log(numSearch);
  if(numSearch === 0){
    return true;
  }
  return numSearch ? true : false;
})

</script>

<template>
  <h1>PRACTICA # 1</h1>
  <div class="text-center mt-3">
    <h2 :class="classCounter">Contador= {{ counter }}</h2>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button>
      <button @click="decrement" class="btn btn-danger">Disminuir</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="blockBtnAdd" class="btn btn-primary">Add</button>
    </div>
  <hr>
  {{ arrayFavoritos }}
  <ul class="list-group">
    <li class="list-group-item" v-for="num in arrayFavoritos"
    :key="index"
    >
    {{ num }}
    </li>
  </ul>
  </div>
</template>

<style>
  h1 {
    background-color: black;
    color: white;
    text-align: center;
    padding: 20px;
  }

  .positive {
    color: green;
  }

  .negative {
    color: red;
  }

  .zero {
    color: blue;
  }
</style>