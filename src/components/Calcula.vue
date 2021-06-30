<template>
  <div>
    <h1>{{ msg }}</h1>
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
    <input type="button" value="Limpar" v-on:click="limpar()">
  </div>
  <div>
    <h3>Prestações: 12x R${{ doze_meses }} | valor a pagar: R${{ total_12 }}</h3>
    <h3>Prestações: 18x R${{ dezoito_meses }} | valor a pagar: R${{ total_18 }}</h3>
    <h3>Prestações: 24x R${{ vinte_quatro_meses }} | valor a pagar: R${{ total_24 }}</h3>
    <h3>Prestações: 36x R${{ trinta_seis_meses }} | valor a pagar: R${{ total_36 }}</h3>
    <h3>Prestações: 48x R${{ quarenta_oito_meses }} | valor a pagar: R${{ total_48 }}</h3>
    <h3>Prestações: 60x R${{ sessenta_meses }} | valor a pagar: R${{ total_60 }}</h3>
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

        this.doze_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 12)).toFixed(2)
        this.dezoito_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 18)).toFixed(2)
        this.vinte_quatro_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 24)).toFixed(2)
        this.trinta_seis_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 36)).toFixed(2)
        this.quarenta_oito_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 48)).toFixed(2)
        this.sessenta_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 60)).toFixed(2)

        this.total_12 = (this.calcular_total_a_pagar(this.doze_meses, 12)).toFixed(2)
        this.total_18 = (this.calcular_total_a_pagar(this.dezoito_meses, 18)).toFixed(2)
        this.total_24 = (this.calcular_total_a_pagar(this.vinte_quatro_meses, 24)).toFixed(2)
        this.total_36 = (this.calcular_total_a_pagar(this.trinta_seis_meses, 36)).toFixed(2)
        this.total_48 = (this.calcular_total_a_pagar(this.quarenta_oito_meses, 48)).toFixed(2)
        this.total_60 = (this.calcular_total_a_pagar(this.sessenta_meses, 60)).toFixed(2)
      },
      calcular_juros(valVeic, juros){
        return parseFloat((valVeic * juros) / 100)
      },
      calcular_entrada(valVeic, valEntrada){
        return parseFloat(valVeic - valEntrada)
      },
      calcular_parcela(valComEntrada, valJuros, NumParcelas){
        return parseFloat((valComEntrada / NumParcelas) + valJuros)
      },
      calcular_total_a_pagar(valParcela, numParcela){
        return parseFloat(valParcela * numParcela)
      },
      limpar(){
        this.valor_veiculo = "",
        this.valor_entrada = "",
        this.valor_taxa_juros = "",
        this.doze_meses = 0,
        this.dezoito_meses = 0,
        this.vinte_quatro_meses = 0,
        this.trinta_seis_meses = 0,
        this.quarenta_oito_meses  = 0,
        this.sessenta_meses = 0,
        this.total_12 = 0,
        this.total_18  = 0,
        this.total_24 = 0,
        this.total_36 = 0,
        this.total_48 = 0,
        this.total_60 = 0
      }
  }
}
</script>

<style scoped>
.calc{
    padding: 10px;
    max-width: 600px;
}
input{
    margin: 10px;
}

</style>
