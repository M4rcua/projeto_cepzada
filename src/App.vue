<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.endereco = data;
    },
  },
};
</script>
<template>
  <h1>Buscar Cep</h1>
  <div>
    <form @submit.prevent="buscar">
      <input type="text" v-model="cep" />
      <button type="submit">Buscar</button>
    </form>
    <form>
      <label for="rua">Rua</label>
      <input name="rua" type="text" v-model="endereco.logradouro" /><br>
      <label for="numero">Numero</label>
      <input name="numero" type="text" v-model="endereco.numero" /><br>
      <label for="localidade">Cidade</label>
      <input for="localidade" type="text" v-model="endereco.localidade" /><br>
      <label for="complemento">Complemento</label>
      <input name="complemento" type="text" v-model="endereco.logradouro" />
    </form>
  </div>
  {{ endereco }}
</template>

<style>
* {
  justify-content: center;
}
</style>
