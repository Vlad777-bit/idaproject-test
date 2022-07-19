<template>
  <label class="form__label" :for="id">{{ label }}</label>
  <textarea
    class="form__description"
    :name="id"
    :id="id"
    :placeholder="placeholder"
  ></textarea>
</template>

<script>
export default {
  name: "CustomInput",

  props: {
    label: {
      type: String,
      required: true,
    },

    id: {
      type: String,
      required: true,
    },

    placeholder: {
      type: String,
      require: false,
    },
  },
};
</script>
