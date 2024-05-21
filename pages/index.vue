<template>
  <div class="main-container">
    <v-container v-if="currentView === 'home'" class="home-container">
      <CustomCarousel />

      <v-row justify="center" class="info-section">
        <v-col cols="12" md="6">
          <v-card class="info-card" color="#E57D90" dark>
            <v-row align="center">
              <v-col cols="2">
                <v-img src="/imagenes/Sale.png" alt="Sale Logo" contain height="50"></v-img>
              </v-col>
              <v-col>
                <v-card-title class="text-center">Ofertas</v-card-title>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
        <v-col cols="12" md="6">
          <v-card class="info-card" color="#E57D90" dark>
            <v-row align="center">
              <v-col cols="2">
                <v-img src="/imagenes/Truck.png" alt="Truck Logo" contain height="50"></v-img>
              </v-col>
              <v-col>
                <v-card-title class="text-center">Envíos a todo México</v-card-title>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>

      <v-row justify="center" class="products-grid">
        <v-col cols="12" sm="6" md="4" v-for="product in products" :key="product.id">
          <v-card class="product-card">
            <v-img v-if="product.imageUrl" :src="product.imageUrl" :alt="product.name" class="product-image" contain></v-img>
            <v-card-title class="product-title">{{ product.description }}</v-card-title>
            <v-card-subtitle class="product-subtitle">{{ product.talla }}</v-card-subtitle>
            <v-card-text class="product-price">{{ product.Precio }}</v-card-text>
            <v-btn color="#DF163B" dark class="order-btn" @click="goToOrderPage(product)">Ordenar</v-btn>
          </v-card>
        </v-col>
      </v-row>

      <v-row justify="center" class="mt-5">
        <v-col cols="12">
          <v-img src="/imagenes/Path.jpg" alt="Path"></v-img>
        </v-col>
      </v-row>
    </v-container>

    <OrderPage 
      v-if="currentView === 'order'" 
      :product="selectedProduct" 
      @change-view="currentView = $event"
    />
  </div>
</template>

<script>
import CustomCarousel from '~/components/CustomCarousel.vue';
import OrderPage from '~/components/OrderPage.vue';

export default {
  components: {
    CustomCarousel,
    OrderPage
  },
  data() {
    return {
      currentView: 'home',
      selectedProduct: null,
      products: [
        { id: 1, description: 'BLUSA LILA', talla: 'Tallas M G', Precio: '120MXN', imageUrl: '/imagenes/blusa lila.png' },
        { id: 2, description: 'FALDA CIRCULAR ROSA', talla: 'Tallas CH M G', Precio: '260MXN', imageUrl: '/imagenes/falda rosa.png' },
        { id: 3, description: 'BLUSA NUDE', talla: 'Tallas CH M G', Precio: '150MXN', imageUrl: '/imagenes/blusa nude.png' },
        { id: 4, description: 'MOCASINES', talla: '22-25', Precio: '350MXN', imageUrl: '/imagenes/mocasines.jpg' },
        { id: 5, description: 'SHORT NEGRO', talla: 'Tallas CH M', Precio: '430MXN', imageUrl: '/imagenes/Short.png' },
        { id: 6, description: 'FALDA NEGRA', talla: 'Tallas CH M G', Precio: '350MXN', imageUrl: '/imagenes/Falda .png'}
      ]
    };
  },
  methods: {
    goToOrderPage(product) {
      this.selectedProduct = product;
      this.currentView = 'order';
    }
  }
};
</script>

<style scoped>
.main-container {
  padding-bottom: 20px;
}
.home-container {
  padding-top: 20px;
}
.info-section {
  margin-top: 20px;
  margin-bottom: 20px;
}
.text-center {
  text-align: center;
}
.mt-5 {
  margin-top: 3rem;
}
.products-grid {
  margin-top: 20px;
}
.product-card {
  height: 100%;
  padding: 20px;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;
}
.product-card:hover {
  transform: scale(1.05);
}
.info-card {
  border-radius: 10px;
  margin-bottom: 20px;
}
.order-btn {
  margin-top: 10px;
}
.text-body {
  font-size: 16px;
  overflow-wrap: break-word;
}
.product-image {
  border-radius: 10px;
  object-fit: contain;
  max-height: 150px;
}
.product-title {
  font-size: 18px;
  font-weight: bold;
  color: #000;
}
.product-subtitle, .product-price {
  font-size: 16px;
  color: #000;
}
</style>