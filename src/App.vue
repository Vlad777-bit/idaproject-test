<template>
  <div>
    <div class="container">
      <app-header />
      <div class="app__wrapper">
        <app-form />
        <product-list />
        <custom-modal-call-button @click="showModal" />
      </div>
    </div>

    <modal-form v-if="isModal" @click="hideModal" />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppForm from "./components/AppForm.vue";
import ProductList from "./components/ProductList.vue";
import CustomModalCallButton from "./components/UI/CustomModalCallButton.vue";
import ModalForm from "./components/ModalForm.vue";

export default {
  name: "App",

  data() {
    return {
      isModal: false,
    };
  },

  components: {
    AppHeader,
    AppForm,
    ProductList,
    CustomModalCallButton,
    ModalForm,
  },

  methods: {
    showModal() {
      this.isModal = true;
    },

    hideModal() {
      this.isModal = false;
    },
  },
};
</script>
