<template>
  <div class="container">
    <app-header />
    <div class="app__wrapper">
      <app-form />
      <product-list />
    </div>
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppForm from "./components/AppForm.vue";
import ProductList from "./components/ProductList.vue";

export default {
  name: "App",
  components: { AppHeader, AppForm, ProductList },
};
</script>
