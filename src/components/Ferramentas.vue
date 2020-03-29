<template>
<div id="caixa2">
<div>

  <select v-model="caixaSel">
      <option value="" selected disabled>Selecione uma caixa</option> <!-- selecionado debilitado -->
      <option v-for="(caixa, index) in caixinhas" :key="index" :value="index">
          {{ caixa.titulo }}
    </option> <!-- seleciona a caixa pelo index -->
  </select> 
  <div id="paleta">
      <div class="cor" :style="cor" v-for="(cor, index) in cores" :key='index' @click="alteraCor(cor)">

      </div>
  </div>
  <input type="text" placeholder="Digite o nome da caixa" v-model="titulo">
  <button @click="alterarTexto">OK</button>
</div>
</div>
</template>

div#
<script>
export default {
    name: "Ferramentas",
    props: ['caixinhas'], /* puxa la de caxinhas*/
    data: function(){
        return{
            cores: ['background: pink', 'background: yellow', 'background: green'], /* vetor paleta de cores*/
            caixaSel: '',
            titulo:''
        }
    }, methods:{
        alteraCor: function(cor){
            this.$emit('alteraCor', {
                cor: cor,
                caixa: this.caixaSel
            })

            },alterarTexto: function(){
            this.$emit('alterouTexto', {
                titulo: this.titulo,
                caixa: this.caixaSel
            })

        }
    }
}
</script>

<style>
#caixa2{
    border: 1px solid #ffffff;
    width: 350px;
    height: 160px;
    margin: 30px auto 10px auto;
    display: flex;
    flex-wrap: wrap;
}
#paleta{
    width: 300px;
    height: 150px;
    display: flex;

}
.cor{
    width: 60px;
    height: 60px;
    border: 1px solid #ffffff;
    margin-top: 6px;
    margin-left: 7px;
    
}

</style>