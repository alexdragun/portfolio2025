<script setup lang="ts">
import Header from "@/components/layout/Header.vue";
import Footer from "@/components/layout/Footer.vue";
import Cover from "@/components/sections/Cover.vue";
import About from "@/components/sections/About.vue";
import Skills from "@/components/sections/Skills.vue";
import Experience from "@/components/sections/Experience.vue";
import Publications from "@/components/sections/Publications.vue";
import Contact from "@/components/sections/Contact.vue";

const title = ref("Alex Dragun | Portfolio");
const description = ref(
  "Experienced Front-End Developer with 5+ years of experience in creating and implementing web solutions that improve the user experience. Collaborating with cross-functional teams to bring projects from concept to launch."
);

const originURL = useRequestURL().origin;

useSeoMeta({
  title,
  ogTitle: title,
  description,
  ogDescription: description,
  ogImage: `${originURL}/images/profileMeta.webp`,
  twitterCard: "summary_large_image",
});
</script>

<template>
  <div>
    <Header />
    <Cover />
    <div class="bg-[var(--background-lighter)]">
      <About />
      <Skills />
      <Experience />
      <Publications />
      <Contact />
    </div>
    <Footer />
  </div>
</template>
