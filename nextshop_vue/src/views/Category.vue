<template>
  <div class="page-category">
    <div class="columns is-multiline">
      <div class="column is-12">
        <h2 class="is-size-2 has-text-centered">{{ category.name }}</h2>
      </div>

      <ProductComponent
        v-for="product in category.products"
        :key="product.id"
        :product="product"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { toast } from "bulma-toast";
import ProductComponent from "@/components/ProductComponent.vue";

export default {
  name: "Category",
  components: {ProductComponent},
  data() {
    return {
      category: {
        products: [],
      },
    };
  },
  mounted() {
    this.getCategory();
  },
  methods: {
    async getCategory() {
      const categorySlug = this.$route.params.category_slug;

      this.$store.commit("setIsLoading", true);
      await axios
        .get(`/api/v1/products/${categorySlug}`)
        .then((response) => {
          this.category = response.data;

          document.title = this.category.name + " | Nextshop";
        })
        .catch((error) => {
          console.log(error);

          toast({
            message: "Something went wrong. Please try again!",
            type: "is-danger",
            dismissible: true,
            pauseOnHover: true,
            duration: 2000,
            position: "bottom-right",
          });
        });

      this.$store.commit("setIsLoading", false);
    },
  },
};
</script>

<style>
</style>