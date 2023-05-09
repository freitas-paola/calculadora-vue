<script setup>
import { reactive } from "vue";
import Form from "./components/Form.vue";

const state = reactive({
  filtro: "",
  inputA: "",
  inputB: "",
  result: "Resultado",
});

const add = () => {
  if (state.inputA !== "" && state.inputB !== "") {
    return (state.result = parseInt(state.inputA) + parseInt(state.inputB));
  } else {
    return (state.result = "Preencher ambos os campos");
  }
};

const subtract = () => {
  if (state.inputA !== "" && state.inputB !== "") {
    return (state.result = parseInt(state.inputA) - parseInt(state.inputB));
  } else {
    return (state.result = "Preencher ambos os campos");
  }
};

const divide = () => {
  if (state.inputA !== "" && state.inputB !== "") {
    return (state.result = parseInt(state.inputA) / parseInt(state.inputB));
  } else {
    return (state.result = "Preencher ambos os campos");
  }
};

const multiply = () => {
  if (state.inputA !== "" && state.inputB !== "") {
    return (state.result = parseInt(state.inputA) * parseInt(state.inputB));
  } else {
    return (state.result = "Preencher ambos os campos");
  }
};

const filtrarOperacao = () => {
  const { filtro } = state;

  switch (filtro) {
    case "adição":
      return add();
    case "subtração":
      return subtract();
    case "divisão":
      return divide();
    case "multiplicação":
      return multiply();
    default:
      return state.result;
  }
};
</script>

<template>
  <div class="container">
    <main class="bg-light p-3">
      <h1 class="text-center">Calculadora</h1>
      <Form
        :input-a="state.inputA"
        :input-b="state.inputB"
        :filtro="state.filtro"
        :result="state.result"
        :edit-inputA="(event) => (state.inputA = event.target.value)"
        :edit-inputB="(event) => (state.inputB = event.target.value)"
        :filter="(event) => (state.filtro = event.target.value)"
        :filtrar-operacao="filtrarOperacao()"
      />
    </main>
  </div>
</template>
