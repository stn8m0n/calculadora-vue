<script setup>
import { reactive, computed } from 'vue';

const estado = reactive({
  numero1: '',
  numero2: '',
  operacao: 'soma',
});

const calculaResultado = computed(() => {
  const { numero1, numero2, operacao } = estado;
  switch (operacao) {
    case 'soma':
      return numero1 + numero2;
    case 'subtracao':
      return numero1 - numero2;
    case 'multiplicacao':
      return numero1 * numero2;
    case 'divisao':
      return numero2 !== 0 ? numero1 / numero2 : 'Erro: Divisão por zero';
    default:
      return 0;
  }
});
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1>Calculadora Vue</h1>
    </header>
    <div class="row mb-3">
      <div class="col">
        <input v-model.number="estado.numero1" type="number" placeholder="Digite o número 1" class="form-control" />
      </div>
      <div class="col">
        <input v-model.number="estado.numero2" type="number" placeholder="Digite o número 2" class="form-control" />
      </div>
    </div>
    <div class="row mb-3">
      <div class="col">
        <select v-model="estado.operacao" class="form-control">
          <option value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <h2 class="p-5 mb-4 mt-4 bg-light rounded-3">Resultado: {{ calculaResultado }}</h2>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

header {
  text-align: center;
}

h2 {
  text-align: center;
  margin-top: 20px;
}

/* Remove as setas dos inputs do tipo number */
input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}
</style>
