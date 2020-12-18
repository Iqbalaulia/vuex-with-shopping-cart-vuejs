<template>
  <div>
    <ul class="list-group">
      <li
        class="list-group-item"
        v-for="(item, index) in cart"
        :key="`${index}-cart`"
      >
        <button
          @click="removeItem(item.id)"
          type="button"
          class="close"
          data-dismiss="modal"
          aria-label="Close"
        >
          <span aria-hidden="true">&times;</span>
        </button>
        <div class="media">
          <img width="80px" :src="item.imgUrl" class="mr-3" alt="" />
          <div class="media-body">
            <p class="mt-0">
              {{ item.title }}
            </p>
            <button
              @click="addQty(item.id)"
              class="btn btn-sm btn-primary w-25"
            >
              +
            </button>
            x {{ item.qty }}
            <button
              @click="reduceQty(item.id)"
              class="btn btn-sm btn-primary w-25"
            >
              -
            </button>
          </div>
        </div>
      </li>
    </ul>
    <button
      class="w-100 btn mt-2  btn-lg btn-block btn-success"
      v-if="cart.length"
    >
      Checkout ${{ totalPrice }}
    </button>
  </div>
</template>
<script>
import { mapActions, mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters(["cart"]),
    totalPrice() {
      return this.cart.reduce((a, b) => a + b.qty * b.price, 0);
    },
  },
  methods: {
    ...mapActions(["addQty", "reduceQty", "removeItem"]),
  },
};
</script>
<style scoped>
.media {
  width: 90%;
}

.media-body {
  text-align: left;
}
</style>
