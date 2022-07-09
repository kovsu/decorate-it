<script setup lang="ts">
import { useToggle } from "@vueuse/core";
import { isDark } from "../composables/data";

const toggleDark = useToggle(isDark);
</script>

<template>
  <header class="header">
    <a href="https://github.com/vworldown/decorate-it" target="_blank"
      ><font-awesome-icon
        icon="fa-brands fa-github"
        class="icon"
        :class="{ active: isDark }"
    /></a>
    <button @click="toggleDark()">
      <font-awesome-icon
        icon="fa-solid fa-sun"
        v-if="isDark"
        class="icon"
        :class="{ active: isDark }"
      />
      <font-awesome-icon
        icon="fa-solid fa-moon"
        v-else
        class="icon"
        :class="{ active: isDark }"
      />
    </button>
  </header>
</template>

<style lang="scss" scoped>
.header {
  padding: 1rem 2rem;
  display: flex;
  gap: 2rem;
  align-items: center;
  justify-content: flex-end;
  border-bottom: 1px solid rgba($color: $border-clr, $alpha: 0.8);

  button {
    cursor: pointer;
    border: none;
    background: transparent;
  }
}

.icon {
  font-size: 1.5em;
  color: inherit;
  color: #111;
}

.active {
  color: #fff;
}
</style>
