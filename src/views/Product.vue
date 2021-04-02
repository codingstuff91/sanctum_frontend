<template>
  <div>
    <h1>Liste des produits</h1>
    <ul>
      <li v-for="product in products" :key="product.id">{{ product.name }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

const BASE_URL = "http://localhost:8000/api"
  export default {
    data() {
      return {
        products: []
      }
    },
    mounted () {
      axios.get(BASE_URL + '/products').then((response)=>{
        this.products = response.data
      })
    },
  }
</script>

<style lang="scss" scoped>

</style>
