<template>
  <div id="app">

    <nav>
      <div class="nav-wrapper blue darken-1">
        <a href="#" class="brand-logo center">Agendamento Transferências</a>
      </div>
    </nav>

    <div class="container">
      
      <ul>
        <li v-for="(erro, index) of errors" :key="index">
          <b>{{ erro }}</b> 
        </li>
      </ul>
      
      
      <form @submit.prevent="salvar">

          <label>Conta destino</label>
          <input type="text" placeholder="Conta destino" v-model="transferencia.contaDestino">
          <label>Conta origem</label>
          <input type="number" placeholder="Conta origem" v-model="transferencia.contaOrigem">
          <label>Data agendamento</label>
          <input type="text" placeholder="yyyy-mm-dd" v-model="transferencia.dataAgendamento">
          <label>Data transferência</label>
          <input type="text" placeholder="yyyy-mm-dd" v-model="transferencia.dataTransferencia">
          <label>Dia</label>
          <input type="text" placeholder="Dia" v-model="transferencia.dia">
          <label>Valor</label>
          <input type="text" placeholder="Valor" v-model="transferencia.valor">
          <button class="waves-effect waves-light btn-small">Salvar<i class="material-icons left">save</i></button>

      </form>

      <table>

        <thead>

          <tr>
            <th>CONTA DESTINO</th>
            <th>CONTA ORIGEM</th>
            <th>DATA AGENDAMENTO</th>
            <th>DATA TRANSFERÊNCIA</th>
            <th>DIA</th>
            <th>VALOR</th>
          </tr>

        </thead>

        <tbody>

          <tr v-for="transferencia of transferencias" :key="transferencia.id">

            <td>{{ transferencia.contaDestino }}</td>
            <td>{{ transferencia.contaOrigem }}</td>
            <td>{{ transferencia.dataAgendamento }}</td>
            <td>{{ transferencia.dataTransferencia }}</td>
            <td>{{ transferencia.dia }}</td>
            <td>{{ transferencia.valor }}</td>
            
          </tr>

        </tbody>
      
      </table>

    </div>

  </div>
</template>

<script>

import Transferencia from './service/transferencias';

export default{
  
  data(){
    return{
      transferencia: {
        contaDestino: '',
        contaOrigem: '',
        dataAgendamento: '',
        dataTransferencia: '',
        valor: '' 
      },
      
      transferencias: [],
      errors: []
    }
  },

  mounted(){
    this.listar()
  },

  methods:{

    listar(){
      Transferencia.listar().then(resposta =>{
      this.transferencias = resposta.data
      })
    
  },

    salvar(){

      Transferencia.salvar(this.transferencia).then(resposta => {
        this.transferencia = {}
        alert('Agendamento realizado com sucesso!')
        this.listar()
      }).catch(e => {
        console.log(e.response)
        this.errors = e.response.data.errors
      })
      
    }

  }

}

</script>

<style>
</style>
