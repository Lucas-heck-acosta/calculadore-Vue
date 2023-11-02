<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue'
import Numeros from './components/Numeros.vue'
import Resultado from './components/Resultado.vue'


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
    <Cabecalho/>
    <Numeros :estado="estado" :calc="calc"/>
    <Resultado :resultado="estado.resultado"/>
  </div>
</template>

<style scoped>
</style>
