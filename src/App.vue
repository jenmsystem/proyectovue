<script setup>
import {ref, computed} from 'vue';
const name = 'Vue dinamico';

const counter = ref(0);

const arrayFavoritos = ref([]);

const increment = () =>{
  counter.value ++;
};
const decrement = () =>{
  counter.value --;
};
const reset = () =>{
  counter.value = 0;
};

const bloquearBtnAdd = computed(()=>{
  const numSearch = arrayFavoritos.value.find(num =>num === counter.value);
  if (numSearch === 0) return true;
  return numSearch ? true:false;
});

const add = () =>{
  arrayFavoritos.value.push(counter.value);
}; 

const classCounter = computed(()=>{
  if(counter.value === 0){
      return 'zero';
  }
  if(counter.value > 0){
    return 'positive';
  }
  if(counter.value < 0){
    return 'negative';
  }
});

</script>

<template>
  <div class="container text-center mt-3">
    <h1>hola {{ name.toUpperCase() }}</h1>
  <h2 :class="classCounter">{{ counter }}</h2>
  <div class="btn-group">
    <button @click="increment" class="btn btn-success">increment</button>
    <button @click="decrement" class="btn btn-danger">Decrement</button>
    <button @click="reset" class="btn btn-secondary">Reset</button>
    <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button>
    
  </div>

  </div>
 
</template>

<style>
h1{
  color: red;
}
.positive{
  color: green;
}
.negative{
  color: red;
}
.zero{
  color: peru;
}
</style>