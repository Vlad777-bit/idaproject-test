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
  name: "CustomTextarea",

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

<style lang="scss">
@import "@/styles/base/vatiables";
@import "@/styles/base/mixins";

.form {
  &__description {
    @include input;

    width: 284px;
    height: 108px;
    resize: none;

    &:focus {
      outline: none;
      background-color: $app-background;
      color: $main-color-text;
    }
  }
}
</style>
