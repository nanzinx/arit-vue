<script setup>
import { ref, computed } from 'vue';

const num1 = ref(0)
const num2 = ref(0)
const operacao = ref('+')

const resultado = computed(() => {
  switch (operacao.value) {
    case '+': return num1.value + num2.value
    case '-': return num1.value - num2.value
    case '*': return num1.value * num2.value
    case '/': 
      return num2.value !== 0 ? (num1.value / num2.value).toFixed(2) : 'Erro: Divisão por zero'
    default: return 0
  }
})
</script>

<template>
  <div class="container">
    <div class="p-5 mb-4 mt-4 bg-light rounded-3">
      <h1 class="mb-4 font-bold text-center">Calculadora Aritmética</h1>
      <input type="number" v-model.number="num1" class="w-full p-2 border rounded text-center" placeholder="Digite o primeiro número" />
      <input type="number" v-model.number="num2" class="w-full p-2 border rounded " placeholder="Digite o segundo número" />
      <select v-model="operacao" class="w-full p-2 border rounded">
        <option value="+">Soma (+)</option>
        <option value="-">Subtração (-)</option>
        <option value="*">Multiplicação (*)</option>
        <option value="/">Divisão (/)</option>
      </select>
      <div class="text-center mt-4">
        <p class="text-lg">Resultado: <strong>{{ resultado }}</strong></p>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
