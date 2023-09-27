<script setup>
import { reactive } from 'vue';

const items = reactive({
  nome: [''],
  nomeAAdicionar: '',
  saldo: 1000000,
  saldoATranferir: 0,
  saldosTransferidos: '',
})

// function adicionaNome() {
//   if (items.nomeAAdicionar.length >= 3) {
//     items.nome.push(items.nomeAAdicionar)
//   } else {
//     alert('adicione mais caracteres')
//   }
// }

function transfere() {
  if (items.saldoATranferir <= items.saldo) {
    return items.saldo - items.saldoATranferir;
  } else {
    return items.saldo - items.saldoATranferir;
  }
}

function adicionaContato() {
  if (items.nomeAAdicionar.length <= 6) {
    return 'n';
  } else {
    return items.saldo - items.saldoATranferir;
  }
}

function adicionaNome() {
  return items.nome.push(items.nomeAAdicionar);
}

const chain = reactive({
  transacao: [''],
  transacaoAAdicionar: '',
})

function transferir() {
  return chain.transacao.push(chain.transacaoAAdicionar);
}

</script>

<template>
  <div class="content">
    <div class="containerFluid">
      <div class="p-3 border border-secondary bg-light">
        <h2>Insira uma chave Pix:</h2>
        <input type="text" @keyup="evento1 => items.nomeAAdicionar = evento1.target.value" class="col-7">
        <button v-if="items.nomeAAdicionar.length >= 6" class="btn btn-success col-5"
          @click="adicionaNome()">Próximo</button>
        <button v-else class="btn btn-danger col-5">Próximo</button>
      </div>
      <div class="bg-light p-3">
        <div class="container-fluid border border-secondary p-3 ">
          <h5>Jonas Sopina de Amois</h5>
          <p v-for="evento2 in items.nome"> {{ evento2 }} </p>
          <p>Banco N26</p>
          <p><span>Ag. 0001 </span> | <span>CC: 000007</span></p>
        </div>
        <div class="container-fluid mt-3">
          <p>Saldo: {{ items.saldo }}</p>
          <p>SaldoFinal: {{ transfere() }}</p>
          <input class="col-8" type="number" @keyup="evento => items.saldoATranferir = evento.target.value">
          <button v-if="items.saldoATranferir <= items.saldo" class="btn btn-success col-4" @click="transferir()">Transferir</button>
          <button v-else class="btn btn-danger col-4">Saldo insuficiente</button>
          <!-- kklkl -->

          <!-- <input type="text" @keyup="evento1 => items.nomeAAdicionar = evento1.target.value" class="col-7">
          <button class="btn btn-success col-5" @click="adicionaNome()">Próximo</button> -->



        </div>
      </div>
      <div class="bg-light">
        <ul>
          <li v-for="evento3 in chain.transacao">Nome: Jonas Sopina de Amois | {{ evento3 }}</li>
        </ul>

      </div>
    </div>
  </div>
</template>

<style scoped>
.content {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
}

.containerFluid {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  width: 80%;
}

.bg-light {
  margin-left: 15px;
}

@media screen and (max-width:767px) {
  .containerFluid {
    display: block;
    width: 100%;
  }

  .bg-light {
    margin-left: 0;
  }

  h2 {
    margin-left: 10px;
    font-size: 45px;
  }

  .content {
    padding: 10px;
  }
}
</style>
