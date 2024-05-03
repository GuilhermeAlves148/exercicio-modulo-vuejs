<script setup>
import { reactive } from 'vue'
  const estado = reactive({
    valorA: 0,
    valorB: 0,
    resultado: 0,
    operacao: 'escolha',
  },
)

  const mudaOperacao = (event) => {
    estado.operacao = event.target.value;
    calculo();
  }

  const salvaValorA = (event) => {
    estado.valorA = event.target.value;
    calculo();
  }

  const salvaValorB = (event) => {
    estado.valorB = event.target.value;
    calculo();
  }

  const calculo = () => {
    let resultado = 0;
    let { operacao, valorA, valorB } = estado;

  switch(operacao) {
    case 'adicao':
      resultado = parseInt(valorA) + parseInt(valorB);
      break;
    case 'subtracao':
      resultado = parseInt(valorA) - parseInt(valorB);
      break;
    case 'multiplicacao':
      resultado = parseInt(valorA) * parseInt(valorB);
      break;
    case 'divisao':
      resultado = parseInt(valorA) / parseInt(valorB);
      break;
    default:
      resultado = 0;
    }
    estado.resultado = resultado;
  }
</script>

<template>
  <div class="container">
    <header class="p-5 mt-4 mb-4">
      <h1>Calculadora aritmética</h1>
    </header>
    <form class="row">
      <div class="col">
        <input @keyup="salvaValorA" class="form-control" type="number" placeholder="Digite o primeiro valor">
      </div>
      <div class="col">
        <input @keyup="salvaValorB" class="form-control" type="number" placeholder="Digite o segundo valor">
      </div>
      <div class="col">
        <select @change="mudaOperacao" class="form-control" placeholder="Escolha a operação">
          <option>Escolha a operação</option>
          <option value="adicao">(+)Adição</option>
          <option value="subtracao">(-)Subtração</option>
          <option value="multiplicacao">(X)Multiplicação</option>
          <option value="divisao">(/)Divisão</option>
        </select>
      </div>
    </form>
    <h3 class="mt-4">O resultado é: {{ estado.resultado }}</h3>
  </div>
</template>

<style scoped>

</style>
