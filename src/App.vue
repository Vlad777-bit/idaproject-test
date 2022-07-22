<template>
  <div class="container">
    <app-header v-model="selectedSort" :sortOptions="sortOptions" />
    <div class="app__wrapper">
      <app-form @add-product="addNewProduct" />
      <div class="app__empty" v-if="!productList.length">
        Список товаров отсутствует
      </div>
      <product-list
        :products="sortedProducts"
        @remove-product="removeProduct"
      />
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

  created() {
    const productData = localStorage.getItem("product-list");
    if (productData) {
      this.productList = JSON.parse(productData);
    }
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

      selectedSort: "",
      sortOptions: [
        { value: "title", name: "По наименованию" },
        { value: "min", name: "По цене min" },
        { value: "max", name: "По цене max" },
      ],
    };
  },

  watch: {
    productList() {
      localStorage.setItem("product-list", JSON.stringify(this.productList));
    },
  },

  computed: {
    sortedProducts() {
      return [...this.productList].sort((prod1, prod2) =>
        prod1[this.selectedSort]?.localeCompare(prod2[this.selectedSort])
      );
    },
  },

  methods: {
    addNewProduct(newProduct) {
      this.productList = [...this.productList, newProduct];
    },

    removeProduct(id) {
      this.productList = this.productList.filter((p) => p.id !== id);
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/base/vatiables";

.container {
  max-width: 1376px;
  margin: 0 auto;
}

.app {
  // если раскоментировать, в chromium появляется прокрутка снизу
  // width: 100vw;
  min-height: 100vh;

  padding: 32px;
  background-color: $app-background;

  &__wrapper {
    position: relative;

    display: grid;
    grid-template-columns: 332px 1fr;
    gap: 16px;
  }

  &__empty {
    font-size: 2em;
    font-weight: 600;
    text-align: center;
  }
}

// Media

@media (max-width: 1100px) {
  .app {
    padding: 15px;

    &__wrapper {
      grid-template-columns: 1fr;
    }
  }
}
</style>
