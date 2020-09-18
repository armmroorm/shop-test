<template>
  <div class="add-to-cart">
    <v-btn block @click="addToCart" color="dark" dark>
      <v-icon left>mdi-cart</v-icon> Add to Cart
    </v-btn>
  </div>
</template>

<script>
import { mapActions } from "vuex";
import { Toast } from "../main";
export default {
  name: "add-to-cart-detail",
  props: {
    name: String,
    price: String,
    image: String,
    pId: String
  },
  data() {
    return {
      item: {
        productName: this.name,
        productImage: this.image,
        productPrice: this.price,
        productId: this.pId,
        productQuantity: 1
      }
    };
  },
  methods: {
    ...mapActions({
      getToCart: "store/getToCart"
    }),
    addToCart() {
      Toast.fire({
        icon: "success",
        title: "Add product to cart success"
      });
      this.getToCart(this.item);
    }
  }
};
</script>

<style></style>
