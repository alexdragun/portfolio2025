<script setup lang="ts">
const activeLink = ref("");
const isMenuOpened = ref(false);

const links = ref([
  { label: "About me", path: "aboutme", type: "link" },
  { label: "Skills", path: "skills", type: "link" },
  { label: "Experience", path: "experience", type: "link" },
  { label: "Publications", path: "publications", type: "link" },
  { label: "Contact me", path: "contactme", type: "link-btn" },
]);

const updateActiveSectionOnScroll = () => {
  const sections = document.querySelectorAll("[id]");
  const buffer = 100; // Adjust buffer as needed

  sections.forEach((section) => {
    const rect = section.getBoundingClientRect();
    if (rect.top <= buffer && rect.bottom >= buffer) {
      activeLink.value = section.id;
    }
  });
};

const scrollToSection = (elementId: string) => {
  let offset = -80;
  const element = document.querySelector(`#${elementId}`);
  if (element) {
    const elementPosition =
      element.getBoundingClientRect().top + window.scrollY;
    const offsetPosition = elementPosition + offset;

    window.scrollTo({
      top: offsetPosition,
    });
  }
  isMenuOpened.value = false;
};

const toggleMenu = () => {
  isMenuOpened.value = !isMenuOpened.value;
};

onMounted(() => {
  window.addEventListener("scroll", updateActiveSectionOnScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", updateActiveSectionOnScroll);
});
</script>

<template>
  <header class="nav">
    <div class="nav__inner">
      <div class="nav__inner-left">
        <a @click="scrollToSection('cover')">
          <img class="logo" src="/images/logo.png" alt="logo" />
        </a>
      </div>
      <div class="nav__inner-right">
        <a
          v-for="(link, index) in links"
          :class="`${link.type} ${activeLink === link.path ? 'active' : ''}`"
          :key="index"
          @click="scrollToSection(link.path)"
          >{{ link.label }}</a
        >
      </div>
      <div
        class="hamburger"
        :class="{ 'hamburger-active': isMenuOpened }"
        @click="toggleMenu"
      >
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
    <transition name="slide-fade">
      <div v-if="isMenuOpened" class="responsive-header">
        <a
          v-for="(link, index) in links"
          :class="`${link.type} ${activeLink === link.path ? 'active' : ''}`"
          :key="index"
          @click="scrollToSection(link.path)"
          >{{ link.label }}</a
        >
      </div>
    </transition>
  </header>
</template>

<style lang="scss" scoped>
.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.4s;
}
.slide-fade-enter-from,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateX(250px);
}

.nav {
  @apply px-5 bg-[var(--header)] fixed top-0 right-0 left-0 z-50;
  .link {
    @apply block cursor-pointer mb-4 md:mb-0;
    &:hover {
      &:after {
        @apply w-[25px];
      }
    }
    &:after {
      content: "";
      @apply block w-[0px] h-[1px] bg-[var(--white)] duration-300;
    }
    &-btn {
      @apply block w-fit md:ml-2 py-3 px-6 border border-[var(--cyan)] uppercase duration-300 hover:bg-[rgba(255,255,255,0.2)] cursor-pointer;
    }
    &.active {
      @apply text-[var(--cyan)];
      &:after {
        @apply w-[25px];
      }
    }
  }
  &__inner {
    @apply py-5 mx-auto max-w-6xl flex justify-between items-center;
    &-left {
      .logo {
        @apply w-12 cursor-pointer;
      }
    }
    &-right {
      @apply hidden items-center gap-7 md:flex;
    }
    .hamburger {
      cursor: pointer;
      @apply block md:hidden;
      &:hover {
        span {
          background-color: var(--cyan) !important;
        }
      }
      &-active {
        span {
          background-color: var(--cyan) !important;
          &:nth-child(1) {
            margin-bottom: -3px !important;
            transform: rotate(45deg) !important;
          }
          &:nth-child(2) {
            @apply opacity-0 -mb-[2px] -translate-x-10;
          }
          &:nth-child(3) {
            margin-bottom: 0 !important;
            width: 30px !important;
            transform: rotate(-45deg) !important;
          }
        }
        &:hover {
          span {
            background-color: var(--white) !important;
          }
        }
      }
      span {
        @apply block h-[3px] w-[30px] mb-[5px] bg-[var(--white)] opacity-100 duration-300 last:mb-0;
      }
    }
  }
  .responsive-header {
    box-sizing: border-box;
    @apply block md:hidden fixed top-24 right-0 bottom-0 px-8 py-2 bg-[var(--black)] w-64;
  }
}
</style>
