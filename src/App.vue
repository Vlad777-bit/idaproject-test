<template>
  <app-header />
  <div class="app__wrapper">
    <app-form />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppForm from "./components/AppForm.vue";

export default {
  name: "App",
  components: { AppHeader, AppForm },
};
</script>
