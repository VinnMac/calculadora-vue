<script setup lang="ts">
  import { reactive } from 'vue';
  import { computed } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Calculadora from './components/Calculadora.vue';

  let valor: number | string = 0;


  const estado = reactive({
    numero1 : 0,
    numero2 : 0,
    operacao : ''
  })

  const resultado = computed (() => {
    const INDETERMINADO = 'Indeterminado';
    const INDEFINIDO = 'Indefinido';

    const { operacao, numero1, numero2 } = estado;

    switch (operacao) {
      case 'adicao':
        valor = numero1 + numero2;
        break;

      case 'subtracao':
        valor = numero1 - numero2;
        break;

      case 'multiplicacao':
        valor = numero1 * numero2;
        break;

      case 'divisao':
        if (numero2 === 0) {
          valor = numero1 === 0
          ? INDETERMINADO
          : INDEFINIDO;
        } else {
          valor = numero1 / numero2;
        }
        break;

      default:
        valor = 0
    }

    return typeof valor === 'number'
    ? Math.round(valor * 100) / 100
    : valor;
  })
</script>

<template>
  <div class="container">
    <Cabecalho />
    <Calculadora :numero1="estado.numero1" :numero2="estado.numero2" :operacao="estado.operacao" :resultadoDaOperacao="resultado" @atualizaNumero1= "valor => estado.numero1 = valor" @atualizaNumero2= "valor => estado.numero2 = valor" @atualizaOperacao="valor => estado.operacao = valor"  />
  </div>
</template>

<style scoped>
  .container {
    max-width: 40rem;
    margin: 0 auto;
    background-color: #0abde3;
    padding: 2rem;
    border-radius: 8px;
  }
</style>
