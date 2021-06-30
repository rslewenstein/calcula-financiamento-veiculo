<template>
  <div>
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
  <div>
    <h3>12x R${{ doze_meses }}, total: R${{ total_12 }}</h3>
    <h3>18x R${{ dezoito_meses }}, total: R${{ total_18 }}</h3>
    <h3>24x R${{ vinte_quatro_meses }}, total: R${{ total_24 }}</h3>
    <h3>36x R${{ trinta_seis_meses }}, total: R${{ total_36 }}</h3>
    <h3>48x R${{ quarenta_oito_meses }}, total: R${{ total_48 }}</h3>
    <h3>60x R${{ sessenta_meses }}, total: R${{ total_60 }}</h3>
  </div>
</template>

<script>
export default {
  name: 'Calcula',
  props: {
    msg: String
  },
  data(){
        return{
            doze_meses: 0,
            dezoito_meses: 0,
            vinte_quatro_meses:0,
            trinta_seis_meses:0,
            quarenta_oito_meses:0,
            sessenta_meses:0,
            total_12:0,
            total_18:0,
            total_24:0,
            total_36:0,
            total_48:0,
            total_60:0
        };
    },
  methods: {
      calcular_total(){
        let tot_juros = this.calcular_juros(this.valor_veiculo, this.valor_taxa_juros)
        let total_com_entrada = this.calcular_entrada(this.valor_veiculo, this.valor_entrada)

        this.doze_meses = (this.calcular_doze_meses(total_com_entrada, tot_juros)).toFixed(2)
        this.dezoito_meses = (this.calcular_dezoito_meses(total_com_entrada, tot_juros)).toFixed(2)
        this.vinte_quatro_meses = (this.calcular_vinte_quatro_meses(total_com_entrada, tot_juros)).toFixed(2)
        this.trinta_seis_meses = (this.calcular_trinta_seis_meses(total_com_entrada, tot_juros)).toFixed(2)
        this.quarenta_oito_meses = (this.calcular_quarenta_oito_meses(total_com_entrada, tot_juros)).toFixed(2)
        this.sessenta_meses = (this.calcular_sessenta_meses(total_com_entrada, tot_juros)).toFixed(2)

        this.total_12 = (this.calcular_total_12(this.doze_meses)).toFixed(2)
        this.total_18 = (this.calcular_total_18(this.dezoito_meses)).toFixed(2)
        this.total_24 = (this.calcular_total_24(this.vinte_quatro_meses)).toFixed(2)
        this.total_36 = (this.calcular_total_36(this.trinta_seis_meses)).toFixed(2)
        this.total_48 = (this.calcular_total_48(this.quarenta_oito_meses)).toFixed(2)
        this.total_60 = (this.calcular_total_60(this.sessenta_meses)).toFixed(2)
      },
      calcular_juros(valVeic, juros){
        return parseFloat((valVeic * juros) / 100)
      },
      calcular_entrada(valVeic, valEntrada){
        return parseFloat(valVeic - valEntrada)
      },
      calcular_doze_meses(valComEntrada, valJuros){
        return parseFloat((valComEntrada / 12) + valJuros)
      },
      calcular_dezoito_meses(valComEntrada, valJuros){
        return parseFloat((valComEntrada / 18) + valJuros)
      },
      calcular_vinte_quatro_meses(valComEntrada, valJuros){
        return parseFloat((valComEntrada / 24) + valJuros)
      },
      calcular_trinta_seis_meses(valComEntrada, valJuros){
        return parseFloat((valComEntrada / 36) + valJuros)
      },
      calcular_quarenta_oito_meses(valComEntrada, valJuros){
        return parseFloat((valComEntrada / 48) + valJuros)
      },
      calcular_sessenta_meses(valComEntrada, valJuros){
        return parseFloat((valComEntrada / 60) + valJuros)
      },
      calcular_total_12(valParcela){
        return parseFloat(valParcela * 12)
      },
      calcular_total_18(valParcela){
        return parseFloat(valParcela * 18)
      },
      calcular_total_24(valParcela){
        return parseFloat(valParcela * 24)
      },
      calcular_total_36(valParcela){
        return parseFloat(valParcela * 36)
      },
      calcular_total_48(valParcela){
        return parseFloat(valParcela * 48)
      },
      calcular_total_60(valParcela){
        return parseFloat(valParcela * 60)
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
