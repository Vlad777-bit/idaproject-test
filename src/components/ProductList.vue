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

  data() {
    return {
      products: [
        {
          id: 1,
          img: "item.png",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 10000,
        },
        {
          id: 2,
          img: "item.png",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 10000,
        },
        {
          id: 3,
          img: "item.png",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 10000,
        },
        {
          id: 4,
          img: "item.png",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 10000,
        },
        {
          id: 5,
          img: "item.png",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 10000,
        },
        {
          id: 6,
          img: "item.png",
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: 10000,
        },
      ],
    };
  },
};
</script>
