<template>
  <main class="wrapper">
    <h1>Products</h1>
    <div class="card-container">
      <ProductCardComponent :key="produto.id"
        v-for="produto in inventario"
        :produto="produto"
        :addCarrinho="addCarrinho"
      />
    </div>
  </main>
</template>

<script>
import ProductCardComponent from '@/components/ProductCard.vue'
export default {
  name: 'ProductView',
  props: ['inventario', 'addCarrinho'],
  components: {
    ProductCardComponent
  }
}
</script>
