<script setup lang="ts">
import TheHeader from "./components/TheHeader.vue";
</script>

<template>
  <TheHeader></TheHeader>
</template>

<style lang="scss">
@import "./styles/main.scss";

html.dark {
  background-color: #111;
}

html.light {
  background-color: #fff;
}
</style>
