<template>
  <div class="product__item" @click="removeProduct(product.id)">
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
</template>

<script>
export default {
  name: "ProductItem",

  props: {
    product: {
      type: Object,
      required: false,
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

<style lang="scss">
@import "@/styles/base/vatiables";

.product {
  &__item {
    width: 332px;
    min-height: 423px;

    background-color: $main-background;

    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
      0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;

    cursor: pointer;
    position: relative;

    &:hover {
      &::after {
        content: url("@/assets/icons/delete.svg");
        padding: 8px 8px 5px 8px;

        position: absolute;
        top: -8px;
        right: -8px;

        background: #ff8484;
        box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
        border-radius: 10px;
      }
    }
  }

  &__img {
    width: 332px;
    height: 200px;

    img {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }
  }

  &__content {
    padding: 16px 16px 24px 16px;
  }

  &__title {
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;

    color: $main-color-text;
  }

  &__description {
    padding-top: 16px;

    font-weight: 400;
    font-size: 16px;
    line-height: 23px;

    color: $main-color-text;
  }

  &__price {
    padding-top: 25px;

    display: block;

    font-weight: 600;
    font-size: 24px;
    line-height: 30px;

    color: $main-color-text;
  }
}
</style>
