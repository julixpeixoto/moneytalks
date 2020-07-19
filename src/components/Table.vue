<template>
  <div class="table">
    <table class="table table-dark table-striped table-hover">
      <thead>
        <tr>          
          <th scope="col">Moeda</th>
          <th scope="col">Valor</th>
          <th scope="col">Tipo</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="dado in dados" v-bind:key="dado">          
          <td>{{dado.name}}</td>
          <td>{{dado.value}}</td>
          <td>{{dado.type}}</td>          
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "Table",
  props: {
    msg: String,
    dados: []
  },
};
</script>

<style scoped></style>
