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
    <h3>Prestações: 12x R${{ doze_meses }} | restante a pagar: R${{ restante_12 }} | total + entrada: R${{ total_12 }} </h3>
    <h3>Prestações: 24x R${{ vinte_quatro_meses }} | restante a pagar: R${{ restante_24 }} | total + entrada: R${{ total_24 }}</h3>
    <h3>Prestações: 36x R${{ trinta_seis_meses }} | restante a pagar: R${{ restante_36 }} | total + entrada: R${{ total_36 }}</h3>
    <h3>Prestações: 48x R${{ quarenta_oito_meses }} | restante a pagar: R${{ restante_48 }} | total + entrada: R${{ total_48 }}</h3>
    <h3>Prestações: 60x R${{ sessenta_meses }} | restante a pagar: R${{ restante_60 }} | total + entrada: R${{ total_60 }}</h3>
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
            vinte_quatro_meses:0,
            trinta_seis_meses:0,
            quarenta_oito_meses:0,
            sessenta_meses:0,
            restante_12:0,
            restante_24:0,
            restante_36:0,
            restante_48:0,
            restante_60:0,
            total_12:0,
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
        this.vinte_quatro_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 24)).toFixed(2)
        this.trinta_seis_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 36)).toFixed(2)
        this.quarenta_oito_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 48)).toFixed(2)
        this.sessenta_meses = (this.calcular_parcela(total_com_entrada, tot_juros, 60)).toFixed(2)

        this.restante_12 = (this.calcular_restante_a_pagar(this.doze_meses, 12)).toFixed(2)
        this.restante_24 = (this.calcular_restante_a_pagar(this.vinte_quatro_meses, 24)).toFixed(2)
        this.restante_36 = (this.calcular_restante_a_pagar(this.trinta_seis_meses, 36)).toFixed(2)
        this.restante_48 = (this.calcular_restante_a_pagar(this.quarenta_oito_meses, 48)).toFixed(2)
        this.restante_60 = (this.calcular_restante_a_pagar(this.sessenta_meses, 60)).toFixed(2)

        this.total_12 = (this.calcular_total_a_pagar(this.valor_entrada, this.restante_12)).toFixed(2)
        this.total_24 = (this.calcular_total_a_pagar(this.valor_entrada, this.restante_24)).toFixed(2)
        this.total_36 = (this.calcular_total_a_pagar(this.valor_entrada, this.restante_36)).toFixed(2)
        this.total_48 = (this.calcular_total_a_pagar(this.valor_entrada, this.restante_48)).toFixed(2)
        this.total_60 = (this.calcular_total_a_pagar(this.valor_entrada, this.restante_60)).toFixed(2)
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
      calcular_restante_a_pagar(valParcela, numParcela){
        return parseFloat(valParcela * numParcela)
      },
      calcular_total_a_pagar(valEntrada, valComJuros){
        return parseFloat(valEntrada) + parseFloat(valComJuros)
      },
      limpar(){
        this.valor_veiculo = "",
        this.valor_entrada = "",
        this.valor_taxa_juros = "",
        this.doze_meses = 0,
        this.vinte_quatro_meses = 0,
        this.trinta_seis_meses = 0,
        this.quarenta_oito_meses  = 0,
        this.sessenta_meses = 0,
        this.restante_12 = 0,
        this.restante_24 = 0,
        this.restante_36 = 0,
        this.restante_48 = 0,
        this.restante_60 = 0,
        this.total_12 = 0,
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
