<template>
  <div>
    <v-app-bar app dark color="#E57D90">
      <v-spacer></v-spacer>
      <v-btn color="#F55A76" @click="goBack">Regresar</v-btn>
    </v-app-bar>
    <v-container>
      <v-row justify="center" class="text-center mt-5">
        <v-col cols="12">
          <h1 class="pink--text">GRACIAS POR SU PREFERENCIA</h1>
          <p class="pink--text">Producto a comprar: {{ product.description }} <br> Precio: {{ product.Precio }}</p>
        </v-col>
      </v-row>
      <v-form ref="form" v-model="valid" class="mt-5">
        <v-row>
          <v-col cols="12">
            <v-text-field label="Nombre" v-model="name" :rules="nameRules" required color="pink"></v-text-field>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <v-text-field label="Correo" v-model="email" :rules="emailRules" required color="pink"></v-text-field>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <v-text-field label="Dirección" v-model="address" :rules="addressRules" required color="pink"></v-text-field>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" class="text-center">
            <v-btn color="#DF163B" dark @click="cancelOrder">Cancelar</v-btn>
            <v-btn color="#F55A76" dark @click="submitOrder">Guardar</v-btn>
          </v-col>
        </v-row>
      </v-form>
    </v-container>
  </div>
</template>

<script>
export default {
  props: {
    product: Object
  },
  data() {
    return {
      valid: false,
      name: '',
      email: '',
      address: '',
      nameRules: [
        v => !!v || 'El nombre es obligatorio',
        v => (v && v.length <= 30) || 'El nombre debe tener menos de 30 caracteres'
      ],
      emailRules: [
        v => !!v || 'El correo es obligatorio',
        v => /.+@.+\..+/.test(v) || 'El correo debe ser válido'
      ],
      addressRules: [
        v => !!v || 'La dirección es obligatoria',
        v => (v && v.length <= 20) || 'La dirección debe tener menos de 20 caracteres'
      ]
    };
  },
  methods: {
    goBack() {
      this.$emit('change-view', 'home');
    },
    cancelOrder() {
      this.$emit('change-view', 'home');
    },
    submitOrder() {
      if (this.$refs.form.validate()) {
        alert('PEDIDO REALIZADO. En los siguientes días nos comunicaremos contigo para la orden de pago. Gracias por tu preferencia.');
        setTimeout(() => {
          this.$emit('change-view', 'home');
          this.resetForm();
        }, 3000);
      }
    },
    resetForm() {
      this.name = '';
      this.email = '';
      this.address = '';
      this.$refs.form.resetValidation();
    }
  }
};
</script>

<style scoped>
.text-center {
  text-align: center;
}
.mt-5 {
  margin-top: 3rem;
}
</style>

