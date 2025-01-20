<script setup lang="ts"></script>

<template>
  <section class="container-custom" id="cover">
    <div class="container-custom__inner">
      <div>
        <p class="mb-7 lg:mb-14 text-4xl text-[var(--cyan)]">Hi, I am</p>
        <h1 class="text-6xl lg:text-8xl mb-2">Alex Dragun</h1>
        <p class="text-2xl">Front-end developer</p>
      </div>
      <img class="profile" src="/images/profile.webp" alt="profile" />
    </div>
  </section>
</template>

<style lang="scss" scoped>
.container-custom {
  @apply mt-14 pb-0;
  &__inner {
    @apply text-center lg:text-left grid grid-cols-1 lg:grid-cols-[600px,1fr] items-center gap-6 justify-center;
    .profile {
      @apply w-full max-w-xl mx-auto lg:mx-0;
    }
  }
}
</style>
