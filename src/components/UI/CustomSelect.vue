<template>
  <select class="header__sort" :value="modelValue" @change="changeOption">
    <option value="" disabled>По умолчанию</option>
    <option v-for="option in options" :key="option.value" :value="option.value">
      {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: "CustomSelect",

  props: {
    modelValue: {
      type: String,
    },

    options: {
      type: Array,
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

<style lang="scss">
@import "@/styles/base/vatiables";

.header {
  &__sort {
    padding: 10px 25px 10px 16px;

    background: url("@/assets/icons/arrow.svg") no-repeat calc(100% - 15px)
      center $main-background;
    right: 10px;
    outline: 0;
    border: none;
    border-radius: 4px;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);

    font-weight: 400;
    font-size: 12px;
    line-height: 17px;
    color: #b4b4b4;

    // Arrow
    -webkit-appearance: none;
    -moz-appearance: none;
    -ms-appearance: none;
    appearance: none;
  }
}

// Media

@media (max-width: 440px) {
  .header {
    &__sort {
      margin-top: 15px;
    }
  }
}
</style>
