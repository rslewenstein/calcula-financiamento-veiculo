<template>
  <div class="calc">
    <h1>{{ msg }}</h1>
    <!-- <v-text>aaaa</v-text> -->
    <div>
        <label>Valor do veículo:</label>
        <input type="text" v-model="valor_veiculo">
    </div>
    <div>
        <label>Valor da entrada:</label>
        <input type="text" v-model="valor_entrada">
    </div>
    <div>
       <label>Taxa de juros:</label>
       <input type="text" v-model="valor_taxa_juros">
    </div>
    
    <input type="button" value="Calcular" v-on:click="calcular_total()">
  </div>
</template>

<script>
export default {
  name: 'Calcula',
  props: {
    msg: String
  },
  methods: {
      calcular_total(){
      // let total_parcial = parseFloat(this.valor_veiculo) - parseFloat(this.valor_entrada)
       let tot_juros = this.calcular_juros(this.valor_veiculo, this.valor_taxa_juros)
       console.log((tot_juros).toFixed(2))
      },
      calcular_juros(valVeic, juros){
        return parseFloat((valVeic * juros) / 100)
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calc{
    padding: 10px;
    max-width: 600px;
}
input{
    margin: 10px;
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
