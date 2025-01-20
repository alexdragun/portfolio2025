<script setup lang="ts"></script>

<template>
  <section class="container-custom" id="portfolio">
    <div class="container-custom__inner"></div>
  </section>
</template>

<style lang="scss" scoped>
.container-custom {
  @apply mt-14 pb-0 h-screen;
  &__inner {
    @apply grid grid-cols-[600px,1fr] items-center gap-6 justify-center;
    .profile {
      @apply w-full max-w-xl;
    }
  }
}
</style>
