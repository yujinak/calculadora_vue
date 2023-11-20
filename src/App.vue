<!-- 
• Criar um projeto utilizando VueJS;
• Este projeto será uma calculadora aritmética;
• Deverá conter dois campos para inserir os números;
• Um campo do tipo select para escolher a operação aritmética;
• Ao alterar os valores o cálculo já deverá ser realizado, sem precisar clicar em nenhum botão;
• Crie um repositório no Github para esta tarefa e nos envie o link pela plataforma.  -->

<script setup>
import { reactive } from "vue";

const estado = reactive({
  operacao: "+",
  resultado: 0,
  input1: 0,
  input2: 0,
});

const calcular = (evento) => {
  let { operacao, input1, input2 } = estado;

  if (estado.operacao === "+") {
    return (estado.resultado = input1 + input2);
  } else if (estado.operacao === "-") {
    return (estado.resultado = input1 - input2);
  } else if (estado.operacao === "*") {
    return (estado.resultado = input1 * input2);
  } else if (estado.operacao === "/") {
    return (estado.resultado = input1 / input2);
  }
};
</script>

<template>
  <div class="box">
    <h1 class="">Calculadora VueJS</h1>
    <div class="container">
      <form class="campos">
        <div class="row">
          <h3>
            <input
              v-model="estado.input1"
              @keyup="calcular"
              @click="calcular"
              type="number"
            />
          </h3>
        </div>

        <div class="row row-operador">
          <h3 class="operador">
            <b>
              {{ estado.operacao }}
            </b>
          </h3>

          <select
            v-model="estado.operacao"
            @keyup="calcular"
            @click="calcular"
            name=""
            id=""
            class="form-control"
          >
            <option value="+">(Adição)</option>
            <option value="-">(Subtração)</option>
            <option value="*">(Multiplicação)</option>
            <option value="/">(Divisão)</option>
          </select>
        </div>

        <h3>
          <input
            v-model="estado.input2"
            @keyup="calcular"
            @click="calcular"
            type="number"
          />
        </h3>
        <div class="row">
          <h2 class="resultado">
            <label for="">Resultado: </label>
            <br />
            <span> {{ estado.resultado }}</span>
          </h2>
        </div>
      </form>
    </div>
  </div>
</template>

<style scoped>
.container {
  margin: 0 auto;
  width: 40%;
  background-color: rgb(7, 156, 156);
  padding: 36px;
  border-radius: 24px;
  border: none;
  transition: 1s;
}
.container:hover {
  background-color: rgba(7, 156, 156, 0.82);
}
h1 {
  margin: 46px;
  text-align: center;
}

h2,
h3 {
  color: white;
  text-align: center;
}
.row-operador {
  display: flex;
  flex-wrap: nowrap;
  background-color: rgb(7, 156, 156);
  border: none;
  border-radius: 8px;
  width: 36%;
  text-align: center;
  margin: 0 auto;
}

.operador {
  background-color: rgb(7, 156, 156);
  border: none;
  border-radius: 8px;
  width: 24%;
  text-align: center;
}

select {
  background-color: rgb(7, 156, 156);
  /* margin: 12px auto; */
  width: 65%;
  color: white;
  border: none;
  text-align: center;
  font-weight: lighter;
}

input {
  background-color: rgb(7, 156, 156);
  border: none;
  border-radius: 8px;
  border-bottom: solid 1px white;
  width: 25%;
  margin: 12px auto;
  color: white;
}

.resultado {
  width: 40%;
  text-align: center;
  margin: 16px auto;
}
</style>
