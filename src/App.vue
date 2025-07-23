<template>
  <div class="campo">
    <label for="cpf">CPF</label>
    <input
      id="cpf"
      type="text"
      v-model="cpf"
      @input="mascararCPF"
      placeholder="000.000.000-00"
      maxlength="14"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';

const cpf = ref('');

function mascararCPF() {
  let val = cpf.value.replace(/\D/g, ''); // Remove tudo que não é número

  if (val.length > 11) val = val.slice(0, 11);

  val = val.replace(/(\d{3})(\d)/, '$1.$2');
  val = val.replace(/(\d{3})(\d)/, '$1.$2');
  val = val.replace(/(\d{3})(\d{1,2})$/, '$1-$2');

  cpf.value = val;
}
</script>

<style scoped>
.campo input {
  padding: 8px;
  font-size: 16px;
  width: 200px;
}
</style>
