<template>
    <div>
      <h1>Cores</h1>
      <table>
          <tr>
              <th>Id</th>
              <th>Nome</th>
              <th>RGB</th>
              <th>Ativo</th>
          </tr>
          <tr v-for="c in cores" :key="c.id">
              <td>{{c.id}}</td>
              <td>{{c.nome}}</td>
              <td>{{c.rgb}}</td>
              <td>{{c.ativo}}</td>
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
              cores: []
          }
      },
      mounted() {
          axios
              .get('https://carros-app-example.herokuapp.com/cor')
              .then(resp => {
                  this.cores = resp.data
                  console.log('1')
              })
          console.log('2')    
      },
      methods: {
          editar(cor) {
              this.$router.push(`/cor-form/${cor.id}`)
          }
      }
  }
  </script>
  
  <style>
  
  </style>