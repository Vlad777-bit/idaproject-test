<template>
  <div>
    <form class="form" @submit.prevent>
      <custom-input
        :label="'Наименование товара'"
        :type-input="'text'"
        :placeholder="'Введите наименование товара'"
        :id="'name'"
        :is-rquired="require"
        :is-valid="productNameIsValid"
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
        :is-rquired="require"
        :is-valid="productPhotoLinkIsValid"
        v-model="productPhotoLink"
        :error-text="'Поле является обязательным'"
      />

      <custom-input
        :label="'Цена товара'"
        :type-input="'text'"
        :placeholder="'Введите цену'"
        :id="'price'"
        :is-rquired="require"
        :is-valid="productPriceIsValid"
        v-model="productPrice"
        :error-text="'Поле является обязательным'"
        @keypress="onlyNumbers"
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
      productNameIsValid: true,

      productDesc: "",

      productPhotoLink: "",
      productPhotoLinkIsValid: true,

      productPrice: "",
      productPriceIsValid: true,

      require: true,
    };
  },

  components: {
    CustomInput,
    CustomTextarea,
    CustomButton,
  },

  watch: {
    productName() {
      if (this.productName.trim().length === 0) {
        this.productNameIsValid = false;
      } else {
        this.productNameIsValid = true;
      }
    },

    productPhotoLink() {
      if (this.productPhotoLink.trim().length === 0) {
        this.productPhotoLinkIsValid = false;
      } else {
        this.productPhotoLinkIsValid = true;
      }
    },

    productPrice() {
      if (this.productPrice.trim().length === 0) {
        this.productPriceIsValid = false;
      } else {
        this.productPriceIsValid = true;

        // Маску не смог реализовать. Реализация ниже, делает разделение не так как ожидается
        // this.productPrice = this.productPrice.replace(
        //   /\B(?=(\d{3})+(?!\d))/g,
        //   " "
        // );
      }
    },
  },

  computed: {
    isDisabled() {
      if (
        this.productName.length &&
        this.productPhotoLink.length &&
        this.productPrice.length
      ) {
        return true;
      }
      return false;
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

    onlyNumbers(event) {
      const keyCode = event.keyCode ? event.keyCode : event.which;
      if (keyCode < 48 || keyCode > 57) {
        event.preventDefault();
      }
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

<style lang="scss">
@import "@/styles/base/vatiables";

.form {
  margin-top: 16px;

  position: fixed;

  width: 332px;
  height: 440px;

  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: flex-start;

  background: $main-background;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04),
    0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  padding: 25px;
}

.reqiredInput {
  &:after {
    content: "";
    display: inline-block;

    position: absolute;
    top: 2px;
    right: -5px;

    width: 4px;
    height: 4px;
    background-color: #ff8484;
    border-radius: 100%;
  }
}

// Media

@media (max-width: 1100px) {
  .form {
    margin: 16px auto;
    position: unset;
  }
}
</style>
