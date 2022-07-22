<template>
  <button class="form__button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "CustomButton",
};
</script>

<style lang="scss">
@import "@/styles/base/vatiables";

.form {
  &__button {
    margin-top: 10px;

    width: 284px;
    height: 36px;

    border: none;
    background: #7bae73;
    border-radius: 10px;

    cursor: pointer;
    transition: $transition;

    // Text
    font-family: "Inter";
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    letter-spacing: -0.02em;
    color: #ffffff;
  }
}
</style>
