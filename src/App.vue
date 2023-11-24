<script setup>

  import { reactive } from 'vue';
  const estado = reactive({
  numeroA: 0,
  numeroB: 0,
  operacao: 'somar',

});

function somar(){
  const numA = parseInt(estado.numeroA);
  const numB = parseInt(estado.numeroB);
  return numA + numB;
}
function restar(){
  const numA = parseInt(estado.numeroA);
  const numB = parseInt(estado.numeroB);
  return numA - numB;
}


function dividir(){
  const numA = parseInt(estado.numeroA);
  const numB = parseInt(estado.numeroB);
  return numA / numB;
}
function multiplicar(){
  const numA = parseInt(estado.numeroA);
  const numB = parseInt(estado.numeroB);
  return numA * numB;
}

function realizarOperacao() {
    switch (estado.operacao) {
      case 'somar':
        return somar();
      case 'restar':
        return restar();
      case 'dividir':
        return dividir();
      case 'multiplicar':
        return multiplicar();
      default:
        return 0;
    }
  }
</script>


<template>
  <header>
    <h1>
      CALCULADORA
    </h1>
  </header>
  <input @keyup="evento => estado.numeroA = evento.target.value" type="number">
  <select v-model="estado.operacao">
    <option value="somar">+</option>
    <option value="restar">-</option>
    <option value="dividir">%</option>
    <option value="multiplicar">x</option>
  </select>
  <input @keyup="evento => estado.numeroB = evento.target.value" type="number">
  <span>{{ realizarOperacao() }}</span>
</template>

<style scoped>
  header {
    background-color: #333;
    color: white;
    text-align: center;
    padding: 10px;
  }

  input, select, span {
    margin: 10px;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }

  select {
    cursor: pointer;
  }

  span {
    display: block;
    font-size: 20px;
    font-weight: bold;
  }


</style>
