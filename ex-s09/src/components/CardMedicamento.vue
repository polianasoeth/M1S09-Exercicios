<!-- EX 07 -->
<template>
    <div class="card">
        <img src="https://media.istockphoto.com/id/635948926/pt/foto/3d-rendering-of-antibiotic-pills-in-blister-pack.jpg?b=1&s=612x612&w=0&k=20&c=7RV73kFAzIeYVgeVLh-lyvilBSOdcV9cqsznXgHN4rs="
            alt="Medicamento" class="medicamento-img">
        <h3>{{ nomeMedicamento }}</h3>
        <p>{{ nomeLaboratorio }}</p>
        <p>Preço: R$ {{ preco }}</p>
        <button @click="favoritar" class="botao-favorito">{{ favorito ? 'Desfavoritar' : 'Favoritar' }}</button>
    </div>
</template>
  
<script>
export default {
    props: {
        nomeMedicamento: String,
        nomeLaboratorio: String,
        preco: Number,
        favorito: Boolean
    },
    methods: {
        favoritar() {
            this.$emit('favoritarMedicamento');
        }
    }
};
</script>
  
<style scoped>
.card {
    border: 1px solid #ccc;
    padding: 10px;
    margin: 10px;
    text-align: center;
}

.medicamento-img {
    max-width: 100px;
    height: auto;
    margin-bottom: 10px;
}

.botao-favorito {
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    padding: 5px 10px;
    cursor: pointer;
    font-size: 14px;
    transition: background-color 0.3s ease-in-out;
}

.botao-favorito:hover {
    background-color: #0056b3;
}
</style>
  