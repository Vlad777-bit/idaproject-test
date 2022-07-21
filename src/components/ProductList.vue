<template>
  <div class="product">
    <div class="product__item" v-for="product in products" :key="product.id">
      <div class="product__img">
        <img
          :src="require(`../assets/img/${product.img}`)"
          :alt="product.title"
        />
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
};
</script>
