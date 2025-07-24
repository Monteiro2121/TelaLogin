<!-- App.vue -->
<template>
  <div class="campo">
    <label for="cpf">CPF</label>
    <input
      type="text"
      id="cpf"
      v-model="cpf"
      @input="mascararCPF"
      placeholder="000.000.000-00"
      maxlength="14"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'

const cpf = ref('')

function mascararCPF() {
  let valor = cpf.value.replace(/\D/g, '') // Remove tudo que não for número
  valor = valor.slice(0, 11) // Limita a 11 dígitos

  if (valor.length > 9) {
    valor = valor.replace(/(\d{3})(\d{3})(\d{3})(\d{1,2})/, '$1.$2.$3-$4')
  } else if (valor.length > 6) {
    valor = valor.replace(/(\d{3})(\d{3})(\d{1,3})/, '$1.$2.$3')
  } else if (valor.length > 3) {
    valor = valor.replace(/(\d{3})(\d{1,3})/, '$1.$2')
  }

  cpf.value = valor
}
</script>


