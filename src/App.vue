<script setup>
import { reactive } from 'vue';

const calcular = reactive({
  numeroA:0,
  numeroB:0,
  actionOp: 'Add',
  resultado:0,
})
function calculadora(){
  if(calcular.actionOp==="Add") calcular.resultado= parseFloat(calcular.numeroA)+parseFloat(calcular.numeroB);
  else if(calcular.actionOp==="Substract")calcular.resultado= parseFloat(calcular.numeroA)-parseFloat(calcular.numeroB);
  else if(calcular.actionOp==="Multiply")calcular.resultado= parseFloat(calcular.numeroA)*parseFloat(calcular.numeroB);
  else if(calcular.actionOp==="Divide")calcular.resultado= parseFloat(calcular.numeroA)/parseFloat(calcular.numeroB);
  return calcular.resultado;


}
</script>

<template>
  <div class="container">
    <h1> Calculadora</h1>
    <div class="app">
      <form>
        {{calcular.numeroA}}
        <input type="number" @input="evento => calcular.numeroA=evento.target.value" placeholder="Digite o Primeiro número">
        {{calcular.numeroB}}
        <input type="number" @input="evento => calcular.numeroB=evento.target.value"placeholder="Digite o Segundo número">
        <div class="opera">
          <h2>Escolha uma operação aritmética</h2>
          <select @change="evento => calcular.actionOp=evento.target.value">
            <option value="Add">Adição</option>
            <option value="Substract">Subtração</option>
            <option value="Multiply">Multiplicação</option>
            <option value="Divide">Divisão</option>
          </select>
        </div>
      </form>
      <div class="result">
        <p>Resultado: {{ calculadora()}}</p>
      </div>
    </div>

  </div>
</template>

<style scoped>
*{
  font-family: 'Courier New', Courier, monospace;
  text-align: center;
}
:global(body){
  background-color: #000;
  color: #fff;
}
.container{
  font-size: 1em;
  font-weight: 800;
  border: 2px solid #fff;
  border-radius: 65px;
  max-width:80vw;
  margin:20% 10%;

}
.container,input{
  display: flex;
  flex-direction: column;
  justify-content:center;
  align-items: center;

}
input,select{
  background-color: #000;
  color: #fff;
  border: 0;
  outline: 1px solid;
  border-bottom: 2px solid;
  text-align: center;
  margin: 10px 150px;

}

</style>
