<template>
  <div class="home">
    <section class="hero is-medium is-dark mb-6">
      <div class="hero-body has-text-centered">
        <p class="title mb-6">
          Welcome to NextShop
        </p>
        <p class="subtitle">
          The best online store for clothes.
        </p>
      </div>
    </section>
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
