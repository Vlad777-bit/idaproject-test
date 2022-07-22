<template>
  <div class="header">
    <div class="header__wrapper">
      <h1 class="header__title">Добавление товара</h1>

      <custom-select
        :value="modelValue"
        @change="changeOption"
        :options="sortOptions"
      />
    </div>
  </div>
</template>

<script>
import CustomSelect from "./UI/CustomSelect.vue";
export default {
  name: "AppHeader",

  components: { CustomSelect },

  props: {
    modelValue: {
      type: String,
      required: false,
      default: "",
    },

    sortOptions: {
      type: Array,
      required: true,
      default: () => [],
    },
  },

  emits: {
    "update:modelValue": (value) =>
      typeof value === "string" && value.length > 0,
  },

  methods: {
    changeOption(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>
