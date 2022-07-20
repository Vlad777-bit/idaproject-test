<template>
  <div>
    <form class="form">
      <custom-input
        :label="'Наименование товара'"
        :typeInput="'text'"
        :placeholder="'Введите наименование товара'"
        :id="'name'"
        :isRquired="true"
      />

      <custom-textarea
        :label="'Описание товара'"
        :placeholder="'Введите описание товара'"
        :id="'description'"
      />

      <custom-input
        :label="'Ссылка на изображение товара'"
        :typeInput="'text'"
        :placeholder="'Введите ссылку'"
        :id="'linkImage'"
        :isRquired="true"
      />

      <custom-input
        :label="'Цена товара'"
        :typeInput="'text'"
        :placeholder="'Введите цену'"
        :id="'price'"
        :isRquired="true"
      />

      <custom-button
        :class="{
          disabled: isDisabled,
        }"
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
      isDisabled: true,
    };
  },

  components: {
    CustomInput,
    CustomTextarea,
    CustomButton,
  },
};
</script>
