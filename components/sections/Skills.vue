<script setup lang="ts">
const skills = ref([
  { label: "Vue.js", imgPath: "/images/skills/vue.png" },
  { label: "Nuxt.js", imgPath: "/images/skills/nuxt.png" },
  { label: "React", imgPath: "/images/skills/react.svg" },
  { label: "Next.js", imgPath: "/images/skills/nextjs.svg" },
  { label: "TypeScript", imgPath: "/images/skills/typescript.png" },
  { label: "Javascript", imgPath: "/images/skills/javascript.png" },
  { label: "Playwright", imgPath: "/images/skills/playwright.svg" },
  { label: "Cypress", imgPath: "/images/skills/cypress.png" },
  { label: "Bootstrap", imgPath: "/images/skills/bootstrap.png" },
  { label: "Vuetify", imgPath: "/images/skills/vuetify.svg" },
  { label: "Quasar", imgPath: "/images/skills/quasar.png" },
  { label: "Figma", imgPath: "/images/skills/figma.png" },
  { label: "Rest API", imgPath: "/images/skills/restapi.svg" },
  { label: "Strapi", imgPath: "/images/skills/strapi.png" },
  { label: "Histoire", imgPath: "/images/skills/histoire.svg" },
  { label: "Storybook", imgPath: "/images/skills/storybook.png" },
  { label: "Git", imgPath: "/images/skills/git.png" },
  { label: "HTML", imgPath: "/images/skills/html5.png" },
  { label: "CSS", imgPath: "/images/skills/css3.png" },
  { label: "Sass", imgPath: "/images/skills/sass.svg" },
]);
</script>

<template>
  <section class="container-custom" id="skills">
    <div class="container-custom__inner">
      <h2 class="line mb-6">Skills</h2>
      <div class="skills">
        <div class="skill" v-for="(skill, index) in skills" :key="index">
          <img :src="skill.imgPath" :alt="skill.label" />
          <p>{{ skill.label }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.container-custom {
  &__inner {
    .skills {
      @apply px-0 grid gap-6 grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5;
      .skill {
        @apply text-center p-6 bg-[var(--grey)] border-b-2 hover:border-[var(--cyan)] duration-300;
        img {
          @apply w-fit h-12 mx-auto;
        }
        p {
          @apply mt-4;
        }
      }
    }
  }
}
</style>
