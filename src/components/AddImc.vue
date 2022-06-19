<template>
  <div class="center">
    <form>
      <div class="inputbox">
        <input type="text" required="required" v-model="name" />
        <span>Seu nome</span>
      </div>
      <div class="inputbox">
        <input type="number" required="required" v-model="height" />
        <span>Sua altura (cm)</span>
      </div>
      <div class="inputbox">
        <input type="number" required="required" v-model="weight" />
        <span>Seu peso (kg)</span>
      </div>
      <div class="inputbox">
        <input type="button" value="Calcular" v-on:click="imcCalc" />
      </div>
    </form>
  </div>
</template>

<script>
import Swal from "sweetalert2";                           //Importa biblioteca de alertas do Vue 3
export default {
  name: "AddImc",
  methods: {
    imcCalc: function () {
      var weight = parseInt(this.weight);
      var height = parseInt(this.height) / 100;
      var imc = weight / (height * height);
      var name = this.name

      if(weight, height, name) {
        if (imc >= 30) {
        return Swal.fire({
          title: `Cuidado, ${name}!! 😮`,
          text: `O seu IMC está no valor de ${imc.toFixed(0)}! Você está acima do peso!`,
          icon: "warning",
        });
      } else {
          return Swal.fire({
          title: `Parabés, ${name} 👏`,
          text: `O seu IMC está no valor de ${imc.toFixed(0)}! Você está no peso ideal!`,
          icon: "success",
        });
      }
      } else {
         return Swal.fire({
          title: `Erro!`,
          text: `Preencha todos os campos para calcular!`,
          icon: "error",
        });
      }
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(45deg, #005db4, #00070e);
  font-family: Avenir, Helvetica, Arial, sans-serif;
}

.center {
  position: relative;
  padding: 50px 50px;
  background: #fff;
  border-radius: 10px;
}
.center h1 {
  font-size: 2em;
  border-left: 5px solid dodgerblue;
  padding: 10px;
  color: #000;
  letter-spacing: 5px;
  margin-bottom: 60px;
  font-weight: bold;
  padding-left: 10px;
}
.center .inputbox {
  position: relative;
  width: 300px;
  height: 50px;
  margin-bottom: 30px;
}
.center .inputbox input {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  border: 2px solid #000;
  outline: none;
  background: none;
  padding: 10px;
  border-radius: 10px;
  font-size: 1.2em;
}
.center .inputbox:last-child {
  margin-bottom: 0;
}
.center .inputbox span {
  position: absolute;
  top: 14px;
  left: 20px;
  font-size: 1em;
  transition: 0.6s;
  font-family: sans-serif;
}
.center .inputbox input:focus ~ span,
.center .inputbox input:valid ~ span {
  transform: translateX(-13px) translateY(-35px);
  font-size: 1em;
}
.center .inputbox [type="button"] {
  width: 100%;
  background: dodgerblue;
  color: #fff;
  border: #fff;
}
.center .inputbox:hover [type="button"] {
  background: linear-gradient(45deg, #005db4, #00070e);
  cursor: pointer;
}
</style>