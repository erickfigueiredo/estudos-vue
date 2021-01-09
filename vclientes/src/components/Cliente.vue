<template>
    <!-- Só é possivel ter uma tag pai dentro de cada componente-->
    <div id="cliente" :class="{'cliente': !isPremium, 'cliente-premium': isPremium}">
        <h2>Descrição: {{desc}}</h2>
        <!-- : interpolação para carregar dados dentro do input (One way data-binding)-->
        <input type="number" name="idade" id="idade" :value="19">
        <hr>
        <!-- Reatividade: Two way data-binding -->
        <input type="email" name="email" id="email" v-model="email">
        <!-- Aplicando o Filtro basta digitar o pipe '|' seguido do metodo de processamento -->
        <h1>{{email | processarEmail}}</h1>
        <h3>{{nome}}</h3>
        <p v-if="showAge"> Aqui ficaria a idade </p>
        <h1 v-else> Esse cara é eterno</h1>
        <hr>
        <!-- Mesmo quando o vshow é falso ele não deleta o elemento, apenas oculta (além disso n tem else)-->
        <p v-show="showIdade">Usando show</p>
        <button @click="mudarCor">Mudar Cor</button>
        <h2>{{idEspecial}}</h2>

    </div>
</template>

<script>
export default {
    // Funcao data retorna valores para serem usados no template do componente
    data() {
        return {
            desc: 'Aprendendo vue!',
            numero: '1234',
            email: 'e@e.com'
        }
    },
    // Define uma propriedade que pode ser modificada em casa instancia do componente
    props: {
        nome: String,
        showAge: Boolean,
    },
    methods: {
        mudarCor () {
            console.log('Aqui poderia estar sendo feita alguma logica')
            // Para se referir a dados dentro do componente use this
        }
    },
    filters: {
        processarEmail(value) {
            return value.toUpperCase();
        }
    },
    computed: {
        idEspecial () {
            return ((this.nome + ' ' + this.showAge).toUpperCase());
        }
    }
}
</script>

<!-- Atributo scopped indica que o estilo se limita ao componente -->
<style scoped>
#cliente {
    text-align: center;
    background-color: black;
    color: purple;
}
</style>