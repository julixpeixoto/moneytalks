<template>
  <div class="container-fluid">
    <h1 class="text-center">{{ nameApp }}</h1>
    <Cards v-bind:dados="dados" />
    <Table v-bind:dados="dados" />
  </div>
</template>

<script>

import Table from './components/Table';
import Cards from './components/Cards';

export default {
  components: {
    Table,
    Cards
  },
  data() {
    return{
      nameApp: 'Moneytalks',
      dados: {}
    }
  },
  created() {
    return fetch('https://api.coingecko.com/api/v3/exchange_rates')
    .then(res => res.json())
    .then(res => this.dados = res.rates)
  }
}
</script>

<style>
  body {
    background-color: #343A40;
  }
  h1{
    color: white;
    margin-top: 30px;
  }


</style>
