<template>
  <div>
    <Header />
    <FormularioNovoMedicamento @adicionarMedicamento="adicionarMedicamento" />

    <div class="lista-medicamentos">
      <CardMedicamento v-for="medicamento in listaMedicamentos" :key="medicamento.id" :nomeMedicamento="medicamento.nome"
        :nomeLaboratorio="medicamento.laboratorio" :preco="medicamento.preco" :favorito="medicamento.favorito"
        @favoritarMedicamento="favoritarMedicamento(medicamento.id)" />
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import FormularioNovoMedicamento from './components/FormularioNovoMedicamento.vue';
import CardMedicamento from './components/CardMedicamento.vue';

export default {
  components: {
    Header,
    FormularioNovoMedicamento,
    CardMedicamento
  },
  data() {
    return {
      listaMedicamentos: []
    };
  },
  methods: {
    adicionarMedicamento(novoMedicamento) {
      novoMedicamento.id = this.listaMedicamentos.length
      novoMedicamento.favorito = false;

      this.listaMedicamentos.push(novoMedicamento);

      console.log('Medicamento cadastrado:', novoMedicamento);
    },

    favoritarMedicamento(id) {
      const medicamento = this.listaMedicamentos[id]

      if (medicamento) {
        medicamento.favorito = !medicamento.favorito;
        console.log('Medicamento favoritado:', medicamento);
      }
    }
  }
}
</script>