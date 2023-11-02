<script setup>
import { def } from '@vue/shared';
import { reactive } from 'vue';

  const estado = reactive({
    x: 0,
    y: 0,
    operacao: 'add',
    resultado: '',
  })

  const calc = () => 
  {
    if(typeof estado.x === 'number' && typeof estado.y === 'number' )
    {
      switch(estado.operacao){
        case 'add':
          estado.resultado = estado.x + estado.y;
          break;
        case 'subtract':
          estado.resultado = estado.x - estado.y;
          break;
        case 'multiply':
          estado.resultado = estado.x * estado.y;
          break;
        case 'divide':
          if(estado.y !== 0){
            estado.resultado = estado.x / estado.y;
          }else {
            estado.resultado = ''
          }
          break;
        default:
          console.log("algo deu errado");
          estado.resultado = '';
          break;
      }
    }
    else
    {
      estado.resultado = '';
    }
  }
</script>

<template>
  <div class="container">
    <header class="p-3 mb-2 mt-4 bg-primary rounded-3 text-center">
      <h1>Calculadora em Vue.js</h1>
      <p>
        Faça seu cálculo:
      </p>
    </header>

    <form>
      <div class="row">
        <div class="col-md-5">
          <input v-model="estado.x" @input="calc" type="number" placeholder="Número 1" class="form-control">
        </div>
        <div class="col-md-2">
          <select v-model="estado.operacao" @change="calc" class="form-control">
            <option value="add">+</option>
            <option value="subtract">-</option>
            <option value="multiply">x</option>
            <option value="divide">/</option>
          </select>
        </div>
        <div class="col-md-5">
          <input v-model="estado.y" @input="calc" type="number" placeholder="Número 2" class="form-control">
        </div>
      </div>
      <div class="row p-5">
        <div class="col-md-12 text-center">
          <h3>Resultado:</h3>
          <h3 class="resultado">{{ estado.resultado }}</h3>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>
</style>
