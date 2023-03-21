<template>
  <div class="home">
    <div class="columns mb-6">
      <div class="column is-one-fifths has-background-white">

          <router-link to="/summer" class="navbar-item">Clothes</router-link>
          <router-link to="/winter" class="navbar-item">Electronic</router-link>
          <router-link to="/winter" class="navbar-item">Funiture</router-link>
          <router-link to="/winter" class="navbar-item">Beauty</router-link>
          <router-link to="/winter" class="navbar-item">Automotive</router-link>

      </div>
      <div class="column is-0"></div>
      <div class="column is-three-fifths has-background-grey">is-three-quarter </div>
      <div class="column is-0"></div>
      <div class="column is-one-fifths has-background-grey">is-three-quarter </div> 
 
    </div>

    <div class="columns is-multiline">
      <div class="column is-12">
        <h2 class="is-size-2 has-text-centered">
          Latest Products
        </h2>
      </div>
      <ProductComponent v-for="product in latestProducts" :key="product.id" :product="product" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
import ProductComponent from '@/components/ProductComponent.vue'

export default {
  name: 'HomeView',
  components: {ProductComponent},
  data() {
    return {
      latestProducts: [],
    }
  },
  mounted() {
    //console.log('Mounted...')
    this.getLatestProducts()

    document.title = 'Home | Nextshop'
  },
  methods: {
    async getLatestProducts() {
      this.$store.commit('setIsLoading', true)

    await axios
      .get('/api/v1/latest-products/')
      .then(response => {
        this.latestProducts = response.data
      })
      .catch(error => {
        console.log(error)
      })

      this.$store.commit('setIsLoading', false)
    },
  }
}

</script>
