<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link">
        <i class="icofont-spoon-and-fork"></i>
        <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link">
        <span>Products</span>
      </router-link>
      <router-link to="/past-orders" class="top-bar-link">
        <span>Past Orders</span>
      </router-link>
    </nav>
    <div class="top-bar-cart-link" @click="toggleSidebar" >
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ totalQuantity }})</span>
    </div>
  </header>
  <router-view
    :inventario="inventario"
    :addCarrinho="addCarrinho"
  />
  <SidebarComponent
    v-if="showSidebar"
    :toggle="toggleSidebar"
    :carrinho="carrinho"
    :inventario="inventario"
    :remove="removeItem"
  />
</template>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>

<script>
// @ referencia a pasta "src" independente do local em que estivermos
import food from '@/food.json'
import SidebarComponent from '@/components/Sidebar.vue'
export default {
  components: {
    SidebarComponent
  },
  data () {
    return {
      inventario: food,
      carrinho: {},
      showSidebar: false
    }
  },
  computed: {
    totalQuantity () {
      return Object.values(this.carrinho).reduce((acc, curr) => {
        return acc + curr
      }, 0)
    }
  },
  methods: {
    addCarrinho (nome, qtdd) {
      if (!this.carrinho[nome]) this.carrinho[nome] = 0
      this.carrinho[nome] += qtdd
    },
    toggleSidebar () {
      this.showSidebar = !this.showSidebar
    },
    removeItem (nome) {
      delete this.carrinho[nome]
    }
  }
}
</script>
