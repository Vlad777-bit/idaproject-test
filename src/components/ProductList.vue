<template>
  <div class="product">
    <transition-group name="product-list">
      <product-item
        v-for="product in products"
        :key="product.id"
        @remove-product="removeProduct"
        :product="product"
      />
    </transition-group>
  </div>
</template>

<script>
import ProductItem from "./ProductItem.vue";
export default {
  name: "ProductList",
  props: {
    products: {
      type: Array,
      required: true,
    },
  },
  emits: {
    "remove-product": (product) =>
      product ? product : console.error("Ошибка при удалении"),
  },
  methods: {
    removeProduct(id) {
      this.$emit("remove-product", id);
    },
  },
  components: { ProductItem },
};
</script>

<style lang="scss" scoped>
.product-list-enter-active {
  animation: product-list-in 0.5s;
}
.product-list-leave-active {
  animation: product-list-in 0.5s reverse;
}
@keyframes product-list-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}
</style>
