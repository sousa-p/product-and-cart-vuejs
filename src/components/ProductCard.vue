<template>
  <div class="card">
    <div class="card-title">{{produto.name}}</div>
    <div class="card-body"><i :class="'icofont-10x icofont-' + produto.icon"></i>
      <form>
        <div class="row">
          <div class="cell"><label>Type:</label></div>
          <div class="cell"><em>{{produto.type}}</em></div>
        </div>
        <div class="row">
          <div class="cell"><label>Price:</label></div>
          <div class="cell">${{produto.price.USD}}</div>
        </div>
        <div class="row">
          <div class="cell"><label>Quantity:</label></div>
          <div class="cell"><input type="number" v-model.number="qtdd"></div>
        </div>
      </form>
    </div>
    <div class="card-footer"><button class="btn btn-light" @click="addCarrinho(produto.name, qtdd);"> Add to cart </button></div>
  </div>
</template>

<script>
export default {
  name: 'ProductCardComponent',
  props: ['produto', 'addCarrinho'],
  data () {
    return {
      qtdd: 0
    }
  }
}
</script>
