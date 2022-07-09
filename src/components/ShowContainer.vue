<script setup lang="ts">
import { ref, watch } from "vue";
import { isDark } from "../composables/data";

const props = defineProps<{
  cssStyle: string;
  paused: boolean;
}>();

const count = ref(0);

watch(
  () => props.paused,
  (newVal) => {
    if (!newVal) {
      let a = props.cssStyle
        .replace(/\r\n/g, "")
        .split("- - - - - - - - - - - - - - - - - -").length;
      console.log(a);
      count.value = count.value === a ? count.value + 1 : a;
      console.log(count.value);
    }
  }
);
</script>

<template>
  <div class="user" :class="{ active: !isDark, 'user-active': count >= 2 }">
    <div class="user__avator">
      <img
        :class="{ 'user__avator-active': count >= 4 }"
        src="https://images.unsplash.com/photo-1657273359563-a140f1618269?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=987&q=80"
        alt=""
      />
    </div>
    <div class="user__info">
      <p class="user__name" :class="{ 'user__name-active': count >= 3 }">
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

.user-active {
  display: flex;
  gap: 2rem;
  justify-content: center;
  align-items: center;
}

.user__name-active {
  font-size: 1.8rem;
  margin-bottom: 2rem;
}

.user__avator-active {
  width: 12rem;
  height: 12rem;
  object-fit: cover;
  border-radius: 50%;
}

@media (max-width: 800px) {
  .user {
    grid-row: 3 / 4;
    grid-column: 2 / 3;
  }
}
</style>
