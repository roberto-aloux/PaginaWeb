<template>
  <v-app-bar app dark color="primary" height="75">
    <v-text-field
      v-model="search"
      placeholder="Buscar"
      hide-details
      filled
      rounded
      class="rounded-0"
      prepend-inner-icon="mdi-magnify"
    ></v-text-field>
    <v-btn height="56px" elevation="0" color="#F99AAA" dark>Buscar</v-btn>
  </v-app-bar>
</template>

<script>
export default {
  data() {
    return {
      search: "",
    };
  },
};
</script>
