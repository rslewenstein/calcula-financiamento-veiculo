<template>
  <div class="calc">
    <h1>{{ msg }}</h1>

    <input type="text" v-model="valor_veiculo" v-bind:placeholder="valVeiculo">
    <input type="text" v-model="valor_entrada" v-bind:placeholder="valEntrada">
    <input type="text" v-model="valor_taxa_juros" v-bind:placeholder="valJuros">
    <input type="button" value="Convert" v-on:click="convert()">
  </div>
</template>

<script>
export default {
  name: 'Calcula',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
/* ul {
  list-style-type: none;
  padding: 0;
} */
/* li {
  display: inline-block;
  margin: 0 10px;
} */
a {
  color: #42b983;
}
</style>
