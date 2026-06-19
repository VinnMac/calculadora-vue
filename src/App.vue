<script setup lang="ts">
  import { reactive } from 'vue';
  import { computed } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Calculadora from './components/Calculadora.vue';


  const estado = reactive({
    numero1 : 0,
    numero2 : 0,
    operacao : ''
  })

  const resultado = computed (() => {
    const { operacao, numero1, numero2 } = estado;

    switch (operacao) {
      case 'adicao':
        return numero1 + numero2;
      case 'subtracao':
        return numero1 - numero2;
      case 'multiplicacao':
        return numero1 * numero2;
      case 'divisao':
        return numero1 / numero2;
      default:
        return 0
    }
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
