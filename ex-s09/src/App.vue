<template>
  <div>
    <Header />
    <FormularioNovoMedicamento @cadastrarMedicamento="cadastrarMedicamento" />
    <FormularioNovoMedicamento @adicionarMedicamento="adicionarMedicamento" />

    <!-- EX 08 -->
    <div class="lista-medicamentos">
      <CardMedicamento v-for="medicamento in listaMedicamentos"
         :key="medicamento.id" 
         :nomeMedicamento="medicamento.nome"
        :nomeLaboratorio="medicamento.laboratorio" 
        :preco="medicamento.preco" 
        :favorito="medicamento.favorito"
        @favoritarMedicamento="favoritarMedicamento(medicamento.id)" />
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import FormularioNovoMedicamento from './components/FormularioNovoMedicamento.vue';
import CardMedicamento from './components/CardMedicamento.vue'; // EX 08

export default {
  components: {
    Header,
    FormularioNovoMedicamento,
    CardMedicamento
  },
  data() {
    // EX 04
    return {
      listaMedicamentos: []
    };
  },
  methods: {
    cadastrarMedicamento(medicamento) {
      console.log('Cadastrar novo medicamento:', medicamento);
    },

    // EX 05
    adicionarMedicamento(novoMedicamento) {
      novoMedicamento.id = this.listaMedicamentos.length + 1;
      novoMedicamento.favorito = false;

      this.listaMedicamentos.push(novoMedicamento);

      console.log('Medicamento cadastrado:', novoMedicamento);
    },
    // EX 06
    favoritarMedicamento(id) {
      const medicamento = this.listaMedicamentos.find(item => item.id === id);

      if (medicamento) {
        medicamento.favorito = !medicamento.favorito;
        console.log('Medicamento favoritado:', medicamento);
      }
    }
  }
}
</script>
