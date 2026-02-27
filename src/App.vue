<script setup>
import { ref } from 'vue'
const contador = ref(0)
const passar = ref(1)
const mensagem = ref('')

function incrementar() {
  const valor = contador.value + passar.value

  if (valor > 10) {
    mensagem.value = 'Contador está no máximo!'
    contador.value = 10
  }
  else {
    contador.value = valor
    mensagem.value = ''
  }
}
function decrementar() {
  const valor2 = contador.value - passar.value

  if (valor2 < 0) {
    mensagem.value = 'Contador está no minimo!'
    contador.value = 0
  }
  else {
    contador.value = valor2
    mensagem.value = ''
  }
}
</script>

<template>
  <div class="contador">
    <h1>O contador é {{ contador }}</h1>
    <div class="campo">
      <label>Valor a incrementar/decrementar: </label>
      <input type="Number" v-model.number="passar" min="1">
    </div>

    <div class="botoes">
      <button @click="incrementar" :disabled="contador >= 10">Incrementar</button>
      <button @click="decrementar" :disabled="contador <= 0">decrementar</button>
    </div>
    <p class="mensagem" v-if="mensagem">
      {{ mensagem }}
    </p>
  </div>

</template>

<style scoped>
.contador {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  gap: 10px;
}

h1 {
  color: #1e3cff;
  margin: 0;
}

.campo {
  display: flex;
  align-items: center;
  gap: 8px;
}

.campo input {
  width: 50px;
  padding: 4px;
  text-align: center;
}

.botoes {
  display: flex;
  gap: 10px;
}

button {
  padding: 10px 20px;
  background-color: #1e3cff;
  color: white;
  border: none;
  border-radius: 6px;
  font-size: 16px;
}

button:disabled {
  background-color: #8c9eff;
  opacity: 0.7;
}

.mensagem {
  color: red;
  margin: 0;
}
</style>
