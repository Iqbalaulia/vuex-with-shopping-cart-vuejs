<template>
  <div class="row">
    <div
      class="card text-left border-0"
      style="width: 18rem;"
      v-for="(item, index) in products"
      :key="`${index}-productList`"
    >
      <img class="card-img-top" :src="item.imgUrl" :alt="item.title" />
      <div class="card-body">
        <p class="card-title">{{ item.title }}</p>
        <p class="card-text">$ {{ item.price }}</p>
        <a
          href="#"
          @click="addToCart(item)"
          class="btn btn-outline-primary w-100"
          >Add to Cart</a
        >
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";
export default {
  name: "ProductList",

  computed: {
    ...mapGetters(["products"]),
  },
  methods: {
    ...mapActions(["getProducts", "addToCart"]),
  },
  mounted() {
    this.getProducts();
  },
};
</script>

<style scoped>
.card {
  padding: 20px;
}
</style>
