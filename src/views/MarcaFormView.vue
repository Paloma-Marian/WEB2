<template>
  <div>
    <h1>Form marcas</h1>
    <form @submit.prevent="salvar()">
        <label for="nome">Nome:</label>
        <input type="text" size="40" required v-model="marca.nome">
    </form>
    <button>Salvar</button>
    <span v-if="msg">{{msg}}</span> <br>
    <p> {{ $route.params.id }} </p>
    <p><button @click="voltar()">Voltar</button> </p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return{
      marca: {
        nome: ''
      },
      msg: null
    }
  },

    mounted() {
      const id = this.$route.params.id
      axios.get(`https://carros-app-example.herokuapp.com/marca/${id}`)
      .the(resp => this.marca = resp.data)
      .catch(error => {
        alert(error)
        this.$router.push("/marca")
      })
    },
    methods: {
        salvar() {
          axios.post('', this.marca)
          .then(() => this.msg = 'Registro gravado')
          .catch(error => this.messagem = `Problema na gravação ${error}`)
        },
        voltar() {
            // this.$router.go(-1)
            this.$router.go(-1)
        }
    }


}
</script>

<style>

</style>