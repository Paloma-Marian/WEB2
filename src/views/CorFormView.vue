<template>
    <div>
      <h1>Form Cores</h1>
      <p> {{ $route.params.id }} </p>
      <p><button @click="voltar()">Voltar</button> </p>
    </div>
  </template>
  
  <script>
  export default {
  
      mounted() {
          console.log(this.$route.params.id)
      },
      methods: {
          voltar() {
              // this.$router.go(-1)
              this.$router.go(-1)
          }
      }
  
  
  }
  </script>
  
  <style>
  
  </style>