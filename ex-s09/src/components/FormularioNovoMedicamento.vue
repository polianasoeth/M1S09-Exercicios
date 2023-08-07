<!-- EX 03 -->
<template>
    <div class="formulario">
        <form @submit.prevent="submitForm">
            <div>
                <label for="nome">Nome do Medicamento:</label>
                <input type="text" id="nome" v-model="medicamento.nome" required>
            </div>
            <div>
                <label for="laboratorio">Nome do Laboratório:</label>
                <input type="text" id="laboratorio" v-model="medicamento.laboratorio" required>
            </div>
            <div>
                <label for="preco">Preço:</label>
                <input type="number" id="preco" v-model="medicamento.preco" required>
            </div>
            <button type="submit">Cadastrar</button>
        </form>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            medicamento: {
                nome: '',
                laboratorio: '',
                preco: 0.00
            }
        };
    },
    methods: {
        submitForm() {
            this.$emit('cadastrarMedicamento', this.medicamento);
            this.$emit('aadicionarMedicamento', this.medicamento);
        }
    }
};
</script>
  
<style>
.formulario {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    background-color: #fff;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 8px;
}

label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
}

input[type="text"],
input[type="number"] {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 14px;
    margin-bottom: 15px;
    transition: border-color 0.3s ease-in-out;
}

input[type="text"]:focus,
input[type="number"]:focus {
    border-color: #007bff;
}

button[type="submit"] {
    width: 350px;
    text-align: center;
    padding: 15px 20px;
    border: 1px solid #eee;
    border-radius: 6px;
    background-color: #FCC302;
    font-size: 18px;

}
</style>


 