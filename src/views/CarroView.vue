<template>
  <div>
    <h1>Carros</h1>
    <table>
        <tr>
            <th>Id</th>
            <th>Nome</th>
            <th>Ano Fabricação</th>
            <th>Ano Modelo</th>
            <th>Preço</th>
            <th>Marca</th>
            <th>Cor</th>
        </tr>
        <tr v-for="c in carros" :key="c.id">
            <td>{{c.id}}</td>
            <td>{{c.nome}}</td>
            <td>{{c.anoFabricacao}}</td>
            <td>{{c.anoModelo}}</td>
            <td>{{c.preco}}</td>
            <td><span v-if="c.marca">{{c.marca.nome}}</span></td>
            <td><span v-if="c.cor">{{c.cor.nome}}</span></td>
            <td><a href="javascript:void(0)" @click="editar(c)">Editar</a></td>
        </tr>
    </table>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            carros: []
        }
    },
    mounted() {
        axios
            .get('https://carros-app-example.herokuapp.com/carro')
            .then(resp => {
                this.carros = resp.data
                console.log('1')
            })
        console.log('2')    
    },
    methods: {
        editar(carro) {
            this.$router.push(`/cor-form/${carro.id}`)
        }
    }
}
</script>

<style>

</style>