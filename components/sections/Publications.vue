<script setup lang="ts">
import moment from "moment";

const publications = ref([
  {
    title: "The importance of testing legacy code: try unit testing",
    date: new Date("05/19/2023"),
    description:
      "Are you struggling with a legacy project that's swarming with bugs? Let us give you an insight into how adding unit tests can make sure these errors bother you no more.",
    url: "https://www.barrage.net/blog/technology/the-importance-of-testing-legacy-code-try-unit-testing",
  },
  {
    title: "Top 8 SASS mixins to speed up your frontend development process",
    date: new Date("04/06/2021"),
    description:
      "One of the challenges in a developer's life is speeding up and automating the development process while keeping high-quality standards. A great solution for front-end developers using SASS is its mixin capability.",
    url: "https://www.barrage.net/blog/technology/top-8-sass-mixins",
  },
]);
</script>

<template>
  <section class="container-custom" id="publications">
    <div class="container-custom__inner">
      <h2 class="text-4xl line mb-6">Publications</h2>
      <div class="publications">
        <a
          class="publication"
          v-for="(publicaton, index) in publications"
          :key="index"
          :href="publicaton.url"
          target="_blank"
        >
          <div class="blur"></div>
          <div class="relative z-10">
            <h3 class="text-2xl mb-1">{{ publicaton.title }}</h3>
            <p class="text-xs mb-3">
              {{ moment(publicaton.date).format("MMM DD, YYYY") }}
            </p>
            <p>{{ publicaton.description }}</p>
          </div>
        </a>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.container-custom {
  @apply py-14 mt-0;
  &__inner {
    .publications {
      @apply mt-12 grid grid-cols-1 md:grid-cols-2 gap-6;
      .publication {
        @apply p-6 relative cursor-pointer;
        &:hover {
          .blur {
            filter: blur(5px);
            box-shadow: inset 0 0 500px rgba(255, 255, 255, 0.4);
            background: #2b968e;
          }
        }
        .blur {
          filter: blur(0px);
          box-shadow: inset 0 0 500px rgba(255, 255, 255, 0);
          background: var(--grey);
          @apply absolute top-0 right-0 left-0 bottom-0 duration-300;
        }
      }
    }
  }
}
</style>
