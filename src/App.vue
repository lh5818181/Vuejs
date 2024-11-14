<script setup>
import { reactive } from 'vue';

const nome = "luis henrique"
const meuObj = {
  nome: "luis",
  filmeFavorito: "Player Number 1"
}

function dizOi(nome) {
  return `${nome}: diz oi`;
}

const enderecoDaImg = "https://www.tfd.nl/wp-content/uploads/2023/01/image-9-1024x768.png";
const imgSuperman = "https://s2-oglobo.glbimg.com/GbqWxbRuybZwvSZ7_FtHVdPiEJ4=/0x0:5120x3407/888x0/smart/filters:strip_icc()/i.s3.glbimg.com/v1/AUTH_da025474c0c44edd99332dddb09cabe8/internal_photos/bs/2022/d/8/3fed8yThW1Bcoi8mRRCA/34518555-sc-rio-de-janeiro-rj-06-06-2013-cena-do-longa-homem-de-aco-sobre-as-origens-do-super-.jpg";

const botaoEstaDesabilitado = false

const gostaDeStarTrek = false
const gostaDoSuperman = false

const estaAutorizado = true

// let contador = 0

const estado = reactive({
  contador: 0,
  email: '',
  saldo: 5000,
  transferindo: 0,
  nomes: ["gian", "luis", "daniel", "will", "monica"],
  nomeAInserir: '',
}) 

function incrementar() {
  estado.contador++;
}

function decrementar() {
  estado.contador--;
}

function alteraEmail(evento) {
estado.email = evento.target.value;
}

function mostraSaldoFuturo() {
  const {saldo, transferindo} = estado;
  return saldo - transferindo;
}

function ValidaValorTransferencia() {
  const {saldo, transferindo} = estado;
  return saldo >= transferindo;
}

function cadastrarNome() {
  if (estado.nomeAInserir.length >= 3) {
    estado.nomes.push(estado.nomeAInserir)
  } else(
    alert('digite mais caracteres')
  )
}


</script>

<template>

  <section>
    <h1>{{ dizOi("paulo") }}</h1>
<img v-if="gostaDeStarTrek" :src="enderecoDaImg" alt="star-trek descovery">
<img v-else-if="gostaDoSuperman" :src="imgSuperman" alt="">
<h2 v-else>Não gosta de herois da DC</h2>

<h1 v-if="estaAutorizado">Bem-vindo</h1>
<h1 v-else>Não possui acesso</h1>

<button :desabled="botaoEstaDesabilitado">Enviar Mensagem</button>

<br />
<hr>

{{ estado.contador }}

<button @click="incrementar" type="button">+</button>
<button @click="decrementar" type="button">-</button>

<br />
<hr>

{{ estado.email }}
<input type="email" @keyup="alteraEmail">


<br />
<hr>

Saldo: {{ estado.saldo }} <br>
Transferindo: {{ estado.transferindo }} <br>
Saldo depois da transferencia: {{ mostraSaldoFuturo() }} <br>
<input class="campo" :class="{invalido: !ValidaValorTransferencia()}" @keyup="evento => estado.transferindo = evento.target.value" type="number" placeholder="Quantia para transferir"/> 
<button v-if="ValidaValorTransferencia()">Transferir</button>
<span v-else>Valor maior que o saldo</span>

  </section>


<br>
<hr>

<ul>
  <li v-for="nome in estado.nomes">
    {{ nome }}
  </li>

  <input @keyup="evento => estado.nomeAInserir = evento.target.value" type="text" placeholder="Digite um novo nome">
  <button @click="cadastrarNome" type="button">Cadastrar nome</button>
</ul>


</template>

<style scoped>

img {
  max-width: 200px;
}

.invalido {
  outline-color: red;
  border-color: red;
}

.campo {
  border: 2px solid #000;
}
</style>
