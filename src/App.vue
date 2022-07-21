<template>
  <div class="container">
    <app-header />
    <div class="app__wrapper">
      <app-form />
      <product-list :products="productList" />
    </div>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppForm from "./components/AppForm.vue";
import ProductList from "./components/ProductList.vue";

export default {
  name: "App",

  components: {
    AppHeader,
    AppForm,
    ProductList,
  },

  data() {
    return {
      productList: [
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
