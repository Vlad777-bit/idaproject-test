<template>
  <div class="product">
    <div
      class="product__item"
      v-for="product in products"
      :key="product.id"
      @click="removeProduct(product.id)"
    >
      <div class="product__img">
        <img :src="product.img" :alt="product.title" />
      </div>

      <div class="product__content">
        <h3 class="product__title">{{ product.title }}</h3>

        <p class="product__description">
          {{ product.description }}
        </p>

        <span class="product__price"> {{ product.price }} руб. </span>
      </div>
    </div>
  </div>
</template>

<script>
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
};
</script>
