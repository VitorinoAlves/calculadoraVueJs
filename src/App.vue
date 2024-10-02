<script setup>

import { reactive } from 'vue';

  const state = reactive({
    firstNumber: 0,
    secondNumber: 0,
    operation:'soma',
    result:0
  });

  const calculateTheoperation = () =>{
    const {operation} = state;

    switch(operation){
      case 'soma':
        state.result = state.firstNumber+state.secondNumber;
        break;
      case 'subtracao':
        state.result = state.firstNumber-state.secondNumber;
        break;
      case 'multiplicacao':
        state.result = state.firstNumber*state.secondNumber;
        break;
      case 'divisao':
        state.result = state.firstNumber/state.secondNumber;
        break;
    }
  };

  function firstNumberChanged(event){
    state.firstNumber=Number(event.target.value);
    calculateTheoperation();
  }

  function firstSecondChanged(event){
    state.secondNumber=Number(event.target.value);
    calculateTheoperation();
  }

  function operationChanged(event){
    state.operation=event.target.value;
    calculateTheoperation();
  }

  

</script>

<template>
  <div class="container">
    <form action="">
      <h1>Calculadora</h1>
      <div class="fields">
        <input :value="state.firstNumber" @keyup="firstNumberChanged" type="number" name="" id="">
        <select name="" id="" @change="operationChanged" >
          <option value="soma">+</option>
          <option value="subtracao">-</option>
          <option value="multiplicacao">*</option>
          <option value="divisao">/</option>
        </select>
        <input :value="state.secondNumber" @keyup="firstSecondChanged" type="number" name="" id="">
      </div>
      
      <p>Resultado: {{ state.result }}</p>
    </form>
  </div>
</template>

<style scoped>
  .container{
    max-width: 1024px;
    height: 90vh;
    margin:0 auto;
    display: flex;
    justify-content: center; /* Centers horizontally */
    align-items: center;     /* Centers vertically */
  }

  h1{
    text-align: center;
  }

  form{
    align-items: center;
  }

  input{
    padding: 8px;
    max-width: 56px;
    font-size: 18px;
  }

  select{
    margin: 0 16px 0;
    font-size: 18px;
  }

  .fields{
    display: flex;
    justify-content: center;
  }

  p{
    text-align: center;
    font-size: 24px;
  }

</style>
