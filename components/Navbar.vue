<template>
    <v-app-bar app dark color="#F55A76">
      <v-text-field  background-color="#fff" v-model="search" label="Buscar..." hide-details solo-inverted></v-text-field>
      <v-btn color="#F99AAA" dark>Buscar</v-btn>
    </v-app-bar>
  </template>
  
  <script>
  export default {
    data() {
      return {
        search: '',
      }
    }
  }
  </script>
  
  <style scoped>
  .v-text-field {
    background-color: #fff;
    width: 30px;
  }

  </style>