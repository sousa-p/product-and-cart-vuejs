<template>
  <h1>Home</h1>
  <div class="splash-container">
    <div class="splash">
      <h1>Splendid Food</h1>
    </div>
  </div>

  <main class="wrapper">
    <h2>Recommended</h2>
    <div class="recommended">
      <ProductCardComponent :key="produto.id"
        v-for="produto in inventario.slice(0,3)"
        :produto="produto"
        :addCarrinho="addCarrinho"
      />
    </div>
  </main>
</template>

<script>
import ProductCardComponent from '@/components/ProductCard.vue'
export default {
  name: 'HomeView',
  props: ['inventario', 'addCarrinho'],
  components: {
    ProductCardComponent
  }
}
</script>
