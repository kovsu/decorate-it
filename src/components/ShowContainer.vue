<script setup lang="ts">
import { isDark } from "../composables/data";

</script>

<template>
  <div class="user" :class="{ active: !isDark }">
    <div class="user__avator">
      <img
        src="https://images.unsplash.com/photo-1657273359563-a140f1618269?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=987&q=80"
        alt=""
      />
    </div>
    <div class="user__info">
      <p class="user__name">
        Quinn
      </p>
      <p class="user__sentence">Copy.Steal.Make it better.</p>
    </div>
  </div>
</template>

<style scoped lang="scss">
.user {
  grid-row: 3 / 5;
  grid-column: 2 / 3;
  transform: translate(5rem, -5rem);
  background-color: #111;
  border-radius: 5px;
  border: 1px solid rgba($color: $border-clr, $alpha: 0.2);
  box-shadow: 0 0 0 1px rgb(0 0 0 / 5%), 0 0 30px 1px rgb(0 0 0 / 15%);
  color: #fff;
  padding: 1rem;
  transition: all 0.5s;

  &.active {
    background-color: #fff;
  }

  &.active .user__info {
    color: #111;
  }

  &__info,
  &__name,
  &__sentence {
    transition: all 0.5s;
  }
}

img {
  width: 10rem;
  height: 10rem;
  border-radius: 5px;
  transition: all 0.5s;
}

.user__sentence {
  color: #999;
}

@media (max-width: 800px) {
  .user {
    grid-row: 3 / 4;
    grid-column: 2 / 3;
  }
}
</style>
