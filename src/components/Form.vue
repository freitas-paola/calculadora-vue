<script setup>
const props = defineProps([
  "filtrarOperacao",
  "inputA",
  "inputB",
  "editInputA",
  "editInputB",
  "filtro",
  "filter",
  "result",
]);
</script>

<template>
  <form>
    <input
      :value="props.inputA"
      @change="props.editInputA"
      type="number"
      placeholder="Adicione um número"
      class="me-3 form-control"
    />
    <span v-if="props.filtro === 'adição'" class="text-center d-block">+</span>
    <span v-else-if="props.filtro === 'subtração'" class="text-center d-block"
      >-</span
    >
    <span v-else-if="props.filtro === 'divisão'" class="text-center d-block"
      >÷</span
    >
    <span
      v-else-if="props.filtro === 'multiplicação'"
      class="text-center d-block"
      >x</span
    >
    <span v-else class="text-center d-block">*</span>
    <input
      :value="props.inputB"
      @change="props.editInputB"
      type="number"
      placeholder="Adicione um número"
      class="form-control"
    />
    <br />
    <select class="mt-3 form-control" @change="props.filter">
      <option value="">Escolha a operação</option>
      <option value="adição">Adição</option>
      <option value="subtração">Subtração</option>
      <option value="divisão">Divisão</option>
      <option value="multiplicação">Multiplicação</option>
    </select>
    <input
      type="number"
      disabled
      :placeholder="props.filtrarOperacao"
      class="mt-3 form-control"
      :class="{ error: props.result === 'Preencher ambos os campos' }"
    />
  </form>
</template>

<style scoped>
.error {
  border: 2px solid red;
}
</style>
