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
