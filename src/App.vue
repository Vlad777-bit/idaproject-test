<template>
  <div class="container">
    <app-header />
    <div class="app__wrapper">
      <app-form @add-product="addNewProduct" />
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
          img: require("./assets/img/item.png"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10 000",
        },
        {
          id: 2,
          img: require("./assets/img/item.png"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10 000",
        },
        {
          id: 3,
          img: require("./assets/img/item.png"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10 000",
        },
        {
          id: 4,
          img: require("./assets/img/item.png"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10 000",
        },
        {
          id: 5,
          img: require("./assets/img/item.png"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10 000",
        },
        {
          id: 6,
          img: require("./assets/img/item.png"),
          title: "Наименование товара",
          description:
            "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
          price: "10 000",
        },
      ],
    };
  },

  methods: {
    addNewProduct(newProduct) {
      this.productList = [...this.productList, newProduct];
    },
  },
};
</script>
