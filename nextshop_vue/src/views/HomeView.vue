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
      <div class="column is-3 flex" v-for="product in latestProducts" :key="product.id">
        <div class="box">
          <figure class="image mb-4">
            <img :src="product.get_thumbnail">            
          </figure>
          <h3 class="is-size-4">{{ product.name }}</h3>
          <p class="is-size-6 has-text-grey">Kshs. {{ product.price }}</p>

          View Details
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

export default {
  name: 'HomeView',
  components: {},
  data() {
    return {
      latestProducts: [],
    }
  },
  mounted() {
    //console.log('Mounted...')
    this.getLatestProducts()
  },
  methods: {
    getLatestProducts() {
      //console.log('After Mounted...')
      //fetch('http://127.0.0.1:8000/api/v1/latest-products/')
      //.then(res => res.json())
      //.then(data => this.latestProducts = data)
      //.catch(err => console.log(error.message))
      axios
      .get('/api/v1/latest-products/')
      .then(response => {
        this.latestProducts = response.data
      })
      .catch(error => {
        console.log(error)
      })
    },
  }
}

</script>

<style scoped>
  .image {
    margin-top: -1.25rem;
    margin-left: -1.25rem;
    margin-right: -1.25rem;
  }

</style>
