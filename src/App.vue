<script setup>
import { reactive } from 'vue';

const estado = reactive({
  operacao: '',
  numero1: '',
  numero2: '',
});

const calcularResultado = () => {
  switch (estado.operacao) {
    case 'soma':
      return Number(estado.numero1) + Number(estado.numero2);
    case 'subtracao':
      return Number(estado.numero1) - Number(estado.numero2);
    case 'multiplicacao':
      return Number(estado.numero1) * Number(estado.numero2);
    case 'divisao':
      return Number(estado.numero1) / Number(estado.numero2);
    default:
      return 0;
  }
};
</script>

<template>
  <div class="container">
    <h1>Calculadora Aritmética</h1>

    <div>
      <label for="numero1">Número 1:</label>
      <input :value="estado.numero1" @input="evento => estado.numero1 = evento.target.value" type="number" id="numero1" />
    </div>

    <div>
      <label for="operacao">Operação:</label>
      <select :value="estado.operacao" @change="evento => estado.operacao = evento.target.value" id="operacao">
        <option value="soma">Soma (+)</option>
        <option value="subtracao">Subtração (-)</option>
        <option value="multiplicacao">Multiplicação (*)</option>
        <option value="divisao">Divisão (/)</option>
      </select>
    </div>

    <div>
      <label for="numero2">Número 2:</label>
      <input :value="estado.numero2" @input="evento => estado.numero2 = evento.target.value" type="number" id="numero2" />
    </div>

    <div>
      <h2>Resultado: {{ calcularResultado() }} </h2>
    </div>
  </div>
</template>

<style scoped>
.container {
  margin: 60px auto;
  max-width: 500px;
  width: 100%;
  padding: 12px 24px;
  background-color: rgb(220, 231, 245);
  border-radius: 12px;
}

h1, h2, label {
  color: rgb(26, 26, 116);
}

input,
select {
  padding: 8px;
  margin: 8px;
}
</style>
