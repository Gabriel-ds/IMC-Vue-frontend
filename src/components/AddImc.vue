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
    <div>
      {{data}}
    </div>
  </div>
</template>

<script>
import Swal from "sweetalert2";
import api from "../services/api";

export default {
  name: "AddImc",
  data() {
    return 
  },
  methods: {
    imcCalc: async function () {
      const weight = parseInt(this.weight);
      const height = parseInt(this.height) / 100;
      const userName = this.name;

      await api.post("/", {
        userName,
        height,
        weight,
      });

      const { data } = await api.get("/");
      console.log(data[data.length - 1].userName);

        if ((weight, height, userName)) {
        return await Swal.fire({
          title: data[data.length - 1].title,
          text: data[data.length - 1].text,
          icon: data[data.length - 1].icon,
          footer: data[data.length - 1].footer,
        });
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
.center .inputbox span,
.center .inputbox span {
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
