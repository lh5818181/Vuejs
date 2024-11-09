<script setup>
const nome = "luis henrique"
const meuObj = {
  nome: "luis",
  filmeFavorito: "Player Number 1"
}

function dizOi(nome) {
  return `${nome}: diz oi`;
}

const enderecoDaImg = "https://www.tfd.nl/wp-content/uploads/2023/01/image-9-1024x768.png"

const botaoEstaDesabilitado = false

const = gostaDeStarTrek = true,
</script>

<template>
<h1>{{ dizOi("paulo") }}</h1>
<img v-if="gostaDeStarTrek" :src="enderecoDaImg" alt="star-trek descovery">

<button :desabled="botaoEstaDesabilitado">Enviar Mensagem</button>
</template>

<style scoped>

</style>
