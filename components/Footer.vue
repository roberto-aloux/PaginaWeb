<template>
  <v-footer color="#F55A76" class="white--text py-4">
    <v-container>
      <v-row justify="center">
        <v-col cols="12" class="text-center">
          <v-img src="/imagenes/logo.png" alt="Logo" contain height="50"></v-img>
        </v-col>
      </v-row>
      <v-row justify="center" class="mt-3">
        <v-col cols="12" sm="3" class="text-center">PRODUCTOS</v-col>
        <v-col cols="12" sm="3" class="text-center">BLOG</v-col>
        <v-col cols="12" sm="3" class="text-center">SHOP</v-col>
        <v-col cols="12" sm="3" class="text-center">CONTACTO</v-col>
      </v-row>
    </v-container>
  </v-footer>
</template>

<script>
export default {
  name: 'Footer'
};
</script>

<style scoped>
.text-center {
  text-align: center;
  color: aliceblue;
}
</style>
