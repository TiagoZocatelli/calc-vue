<template>
    <div class="container">
      <div class="calculator">
        <h1>Calculadora Aritmética</h1>
        <div class="form-group">
          <input v-model.number="num1" type="number" placeholder="Digite o primeiro número" class="form-control" />
        </div>
        <div class="form-group">
          <input v-model.number="num2" type="number" placeholder="Digite o segundo número" class="form-control" />
        </div>
        <div class="form-group">
          <select v-model="operation" class="form-control">
            <option value="add">+</option>
            <option value="subtract">-</option>
            <option value="multiply">*</option>
            <option value="divide">/</option>
          </select>
        </div>
        <div class="result">
          <h2>Resultado: {{ result }}</h2>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  // Criação das referências reativas para os números e a operação
  const num1 = ref(0);
  const num2 = ref(0);
  const operation = ref('add');
  
  // Computed property para calcular o resultado baseado nos inputs
  const result = computed(() => {
    switch (operation.value) {
      case 'add':
        return num1.value + num2.value;
      case 'subtract':
        return num1.value - num2.value;
      case 'multiply':
        return num1.value * num2.value;
      case 'divide':
        return num2.value !== 0 ? num1.value / num2.value : 'Erro: Divisão por zero';
      default:
        return 0;
    }
  });
  </script>
  
  <style scoped>
  /* Estilos para centralizar o conteúdo */
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
  }
  
  .calculator {
    max-width: 400px;
    padding: 20px;
    background: #f9f9f9;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  .form-control {
    width: 100%;
    padding: 8px;
    font-size: 16px;
  }
  
  .result {
    margin-top: 20px;
    text-align: center;
  }
  
  .result h2 {
    margin: 0;
    font-size: 24px;
    font-weight: bold;
  }
  </style>
  