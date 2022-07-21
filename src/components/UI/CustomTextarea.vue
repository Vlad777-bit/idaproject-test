<template>
  <div>
    <label class="form__label" :for="id">{{ label }}</label>
    <textarea
      class="form__description"
      :name="id"
      :id="id"
      :placeholder="placeholder"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    ></textarea>
  </div>
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

    modelValue: {
      type: String,
      required: true,
    },
  },

  emits: ["update:modelValue"],
};
</script>
