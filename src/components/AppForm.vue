<template>
  <div>
    <form class="form" @submit.prevent>
      <custom-input
        :label="'Наименование товара'"
        :type-input="'text'"
        :placeholder="'Введите наименование товара'"
        :id="'name'"
        :is-rquired="true"
        :is-valid="validName"
        v-model="productName"
        :error-text="'Поле является обязательным'"
      />

      <custom-textarea
        :label="'Описание товара'"
        :placeholder="'Введите описание товара'"
        :id="'description'"
        v-model="productDesc"
      />

      <custom-input
        :label="'Ссылка на изображение товара'"
        :type-input="'text'"
        :placeholder="'Введите ссылку'"
        :id="'linkImage'"
        :is-rquired="true"
        :is-valid="validPhotoLink"
        v-model="productPhotoLink"
        :error-text="'Поле является обязательным'"
      />

      <custom-input
        :label="'Цена товара'"
        :type-input="'text'"
        :placeholder="'Введите цену'"
        :id="'price'"
        :is-rquired="true"
        :is-valid="validPrice"
        v-model="productPrice"
        :error-text="'Поле является обязательным'"
      />

      <custom-button
        :class="{
          disabled: !isDisabled,
        }"
        @click="addNewProduct"
      >
        Добавить товар
      </custom-button>
    </form>
  </div>
</template>

<script>
import CustomInput from "./UI/CustomInput.vue";
import CustomTextarea from "./UI/CustomTextarea.vue";
import CustomButton from "./UI/CustomButton.vue";

export default {
  name: "AppForm",

  data() {
    return {
      productName: "",
      productDesc: "",
      productPhotoLink: "",
      productPrice: "",
    };
  },

  components: {
    CustomInput,
    CustomTextarea,
    CustomButton,
  },

  watch: {
    productPrice() {
      // Маску не смог реализовать. Реализация ниже, делает разделение не так как ожидается
      // this.productPrice = this.productPrice.replace(
      //   /\B(?=(\d{3})+(?!\d))/g,
      //   " "
      // );
    },
  },

  computed: {
    validName() {
      return this.productName.length !== 0;
    },

    validPhotoLink() {
      return this.productPhotoLink.length !== 0;
    },

    validPrice() {
      return this.productPrice.length !== 0;
    },

    isDisabled() {
      return (
        this.productName.length &&
        this.productPhotoLink.length &&
        this.productPrice.length
      );
    },
  },

  methods: {
    addNewProduct() {
      const newProduct = {
        id: Date.now(),
        img: this.productPhotoLink,
        title: this.productName,
        description: this.productDesc,
        price: this.productPrice,
      };

      this.$emit("add-product", newProduct);
      this.clearForm();
    },

    clearForm() {
      this.productName = "";
      this.productDesc = "";
      this.productPhotoLink = "";
      this.productPrice = "";
    },
  },

  emits: {
    "add-product": (value) => {
      if (value) {
        return true;
      } else {
        console.error("Ошибка при добавлении");
        return false;
      }
    },
  },
};
</script>
