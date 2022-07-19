<template>
  <label
    class="form__label"
    :class="{
      reqiredInput: isRquired,
    }"
    :for="id"
  >
    {{ label }}
  </label>

  <input
    class="form__input"
    :type="typeInput"
    :id="id"
    :placeholder="placeholder"
  />
</template>

<script>
export default {
  name: "CustomInput",

  props: {
    label: {
      type: String,
      required: true,
    },

    typeInput: {
      type: String,
      required: true,
    },

    id: {
      type: String,
      required: true,
    },

    placeholder: {
      type: String,
      required: false,
    },

    isRquired: {
      type: Boolean,
      required: false,
    },
  },
};
</script>
