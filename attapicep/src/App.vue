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
    async search() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const {data} = await axios.get(url);
      this.endereco = data;
    },
  },
};
  </script>
  
  <template>
    <main>
      <div class="prin-att">
        <h1>Buscar CEP</h1>
        <div class="inp-att">
          <form @submit.prevent="search">
            <input type="text" v-model="cep" />
            <button class="btn-att" @click="search()" type="submit">Buscar</button>
          </form>
          <form class="end">
            <label for="rua">Rua</label>
            <input type="text" v-model="endereco.logradouro"/>
            <label for="rua">Número</label>
            <input type="text" v-model="endereco.numero"/>
            <label for="rua">Bairro</label>
            <input type="text" v-model="endereco.bairro"/>
            <label for="rua">Cidade</label>
            <input type="text" v-model="endereco.cidade"/>
          </form>
          {{ endereco }}
        </div>
      </div>
    </main>
  </template>