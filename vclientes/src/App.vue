<template>
  <div id="app">
    <Cliente nome="Erick" :showAge="true"></Cliente>
    <Cliente nome="Vinícius"></Cliente>
    <Cliente nome="João"></Cliente>
    <Cliente nome="Victor" :showAge="true"></Cliente>
    <br><br>
    <hr>
    <br>
    <!-- Para usar o v-for precisamos de uma key para diferenciar os clientes-->
    <div v-for="(cliente, index) in orderClientes" :key="cliente.id">
      <h1>{{index}}</h1>
      <p>Testando v-for</p>
      <Cliente :nome="cliente.nome" :showAge="true"></Cliente>
      <input type="text" name="nome" id="nome" v-model="cliente.nome">
    </div>
  </div>
</template>

<script>
import _ from 'lodash';
import Cliente from './components/Cliente';

export default {
  name: 'App',
  data () {
    return {
      nomeField: "",
      emailField: "",
      idadeField: "",
      clientes: [
        {
          id: 1,
          nome: 'C1',
          idade: 32
        },
        { id: 2,
          nome: 'C2',
          idade: 33
        },
        {
          id: 3,
          nome: 'C3',
          idade: 34
        }
      ]
    }
  },
  components: {
    Cliente
  },
  computed: {
    orderClientes () {
      return _.orderBy(this.clientes, ['nome'], ['asc']);
    }
  }
}
</script>

<style>
#app {

}
</style>
