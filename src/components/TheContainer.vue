<script setup lang="ts">
import AppIntroduction from "./AppIntroduction.vue";
import ShowContainer from "./ShowContainer.vue";

import { isDark } from "../composables/data";
import TypeIt from "typeit";
import { onMounted, onUpdated, ref } from "vue";

const block = ref<HTMLPreElement>();
const code = ref("");

onMounted(() => {
  new (TypeIt as any)(block.value, {
    speed: 100,
    startDelay: 900,
    afterStep: () => {
      code.value = JSON.parse(
        JSON.stringify(
          block.value!.innerText.replaceAll(String.fromCharCode(160), "")
        )
      );
    },
  })
    .type(`.user {}`, {
      delay: 400,
    })
    .move(-1, {
      delay: 100,
    })
    .break()
    .break()
    .move(-1, {
      delay: 100,
    })
    .type("&nbsp;&nbsp;display: flex;")
    .break()
    .type("&nbsp;&nbsp;gap: 2rem;")
    .break()
    .type("&nbsp;&nbsp;justify-content: center;")
    .break()
    .type("&nbsp;&nbsp;align-items: center;")
    .move(2)
    .pause(500)
    .break()
    .break()
    .type(`.user__name {}`, { delay: 400 })
    .move(-1)
    .break()
    .break()
    .move(-1)
    .type("&nbsp;&nbsp;font-size: 1.8rem;")
    .break()
    .type(`&nbsp;&nbsp;margin-bottom: 2rem;`)
    .move(2)
    .pause(500)
    .break()
    .break()
    .type(`.user__avator img {}`, { delay: 400 })
    .move(-1)
    .break()
    .break()
    .move(-1)
    .type("&nbsp;&nbsp;width: 12rem;")
    .break()
    .type("&nbsp;&nbsp;height: 12rem;")
    .break()
    .type("&nbsp;&nbsp;object-fit: cover;")
    .break()
    .type(`&nbsp;&nbsp;border-radius: 50%;`)
    .move(2)
    .pause(500)
    .go();
});

onUpdated(() => {
  block.value!.scrollTop = block.value!.scrollHeight;
});
</script>

<template>
  <main class="container">
    <AppIntroduction></AppIntroduction>
    <div class="type__container" :class="{ active: isDark }">
      <header class="type__header">
        <p class="status">./decorate-it.md</p>
      </header>
      <div class="type__content" ref="block"></div>
    </div>
    <ShowContainer></ShowContainer>
    <component is="style"> {{ code }} </component>
  </main>
</template>

<style lang="scss" scoped>
.container {
  padding: 2rem;
  width: 90vw;
  height: calc(100vh - 5rem);
  margin: 0 auto;

  display: grid;
  grid-gap: 2rem;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: repeat(3, 2fr) 1fr;
}

.active {
  color: #fff;
}

.type {
  &__container {
    grid-row: 1 / 3;
    grid-column: 2 / 3;
    border-radius: 5px;
    border: 1px solid rgba($color: $border-clr, $alpha: 0.2);
    box-shadow: 0 0 0 1px rgb(0 0 0 / 5%), 0 0 30px 1px rgb(0 0 0 / 15%);
  }

  &__header {
    position: relative;
    padding: 0.5rem 1rem;
    text-align: center;

    &::before {
      content: "";
      position: absolute;
      top: 12px;
      left: 18px;
      width: 0.8rem;
      height: 0.8rem;
      border-radius: 50%;
      background-color: #f95c5b;
      box-shadow: 0 0 0 1px #da3d42, 22px 0 0 0 #fabe3b, 22px 0 0 1px #ecb03e,
        44px 0 0 0 #38cd46, 44px 0 0 1px #2eae32;
    }
  }

  &__content {
    padding: 1rem 2rem;
    width: 100%;
    height: calc(100% - 3rem);
    overflow: auto;

    &::-webkit-scrollbar {
      width: 10px;
      height: 10px;
    }

    &::-webkit-scrollbar-track {
      width: 6px;
      background: rgba(#101f1c, 0.1);
      -webkit-border-radius: 2em;
      -moz-border-radius: 2em;
      border-radius: 2em;
    }

    &::-webkit-scrollbar-thumb {
      background-color: rgba(144, 147, 153, 0.5);
      background-clip: padding-box;
      min-height: 28px;
      -webkit-border-radius: 2em;
      -moz-border-radius: 2em;
      border-radius: 2em;
      transition: background-color 0.3s;
      cursor: pointer;
    }

    &::-webkit-scrollbar-thumb:hover {
      background-color: rgba(144, 147, 153, 0.3);
    }
  }
}

@media (max-width: 800px) {
  .container {
    height: 150vh;
    grid-template-columns: 1fr 4fr 1fr;
    grid-template-rows: repeat(3, 1fr);
  }

  .type__container {
    grid-row: 2 / 3;
    grid-column: 2 / 3;
  }
}
</style>
