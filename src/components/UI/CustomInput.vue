<template>
  <div>
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
      :class="{
        'error-input': !isValid,
      }"
      :type="typeInput"
      :id="id"
      :placeholder="placeholder"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />

    <span class="error-text" v-if="!isValid">{{ errorText }}</span>
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

    isValid: {
      type: Boolean,
      required: false,
    },

    modelValue: {
      type: String,
      required: true,
    },

    errorText: {
      type: String,
      required: false,
    },
  },

  emits: ["update:modelValue"],
};
</script>

<style lang="scss">
@import "@/styles/base/vatiables";
@import "@/styles/base/mixins";

.form {
  &__label {
    position: relative;

    font-weight: 400;
    font-size: 10px;
    line-height: 14px;
    letter-spacing: -0.02em;
  }

  &__input {
    @include input;

    &:focus {
      outline: none;
      background-color: $app-background;
      color: $main-color-text;
    }
  }
}
</style>
