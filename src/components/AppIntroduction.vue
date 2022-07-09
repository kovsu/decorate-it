<script setup lang="ts">
import { isDark } from "../composables/data";
</script>

<template>
  <section class="introduction" :class="{ active: isDark }">
    <div class="introduction__cover">
      <img
        class="introduction__img"
        src="https://images.unsplash.com/reserve/LJIZlzHgQ7WPSh5KVTCB_Typewriter.jpg?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=996&q=80"
        alt=""
      />
    </div>
    <h2 class="introduction__title">Decorate it!</h2>
    <p class="introduction__content">A demo for typewritter.</p>
  </section>
</template>

<style lang="scss" scoped>
.introduction {
  // background-color: rebeccapurple;
  grid-row: 1 / 5;
  grid-column: 1/ 2;

  display: flex;
  gap: 2rem;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  &__cover {
    width: 12rem;
    height: 12rem;
    border-radius: 50%;
    box-shadow: 0 10px 15px rgba($color: #000000, $alpha: 0.2);
  }

  &__img {
    width: 12rem;
    height: 12rem;
    border-radius: 50%;
    object-fit: cover;
  }

  &__title {
    font-size: 3rem;
  }
}

.active {
  color: #fff;
}

@media (max-width: 800px) {
  .introduction {
    grid-row: 1 / 2;
    grid-column: 1 / 4;
  }
}
</style>
