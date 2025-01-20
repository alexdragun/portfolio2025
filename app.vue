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

<style lang="scss">
/* Navbar */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
  background-color: #2c1250;
}

.navbar .logo {
  font-size: 2rem;
  font-weight: bold;
  color: #ffffff;
}

.navbar .nav-links {
  display: flex;
  gap: 20px;
}

.navbar .nav-links a {
  text-decoration: none;
  color: #ffffff;
  font-size: 1rem;
}

/* Header */
.header {
  text-align: center;
  padding: 50px 20px;
}

.header .avatar {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  margin-bottom: 20px;
}

.header .main-title {
  font-size: 2.5rem;
  margin: 0;
  color: #ffffff;
}

.header .highlight {
  color: #ff66c4;
}

.header .subtitle {
  margin: 10px 0 30px;
  font-size: 1.2rem;
  color: #d9d9d9;
}

.header .role-title {
  font-size: 2rem;
  margin: 20px 0;
}

.header .description {
  font-size: 1rem;
  line-height: 1.5;
  color: #d9d9d9;
}

/* Work Experience */
.work-experience {
  padding: 50px 20px;
  text-align: center;
}

.work-experience h2 {
  font-size: 2rem;
  margin-bottom: 30px;
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}

.card {
  background: linear-gradient(145deg, #2c1250, #4f228d);
  border-radius: 10px;
  padding: 20px;
  text-align: center;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.card h3 {
  margin-top: 10px;
  font-size: 1.2rem;
}

.card p {
  font-size: 0.9rem;
  color: #d9d9d9;
  margin: 10px 0;
}

.card button {
  background-color: #693b93;
  color: #ffffff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 0.9rem;
}

/* Skills */
.skills {
  text-align: center;
  padding: 50px 20px;
}

.skills .highlight {
  color: #ff66c4;
}

.skills-icons {
  margin-top: 20px;
  display: flex;
  justify-content: center;
  gap: 20px;
}

/* Projects */
.projects {
  padding: 50px 20px;
}

.projects h2 {
  text-align: center;
  margin-bottom: 30px;
  font-size: 2rem;
}

.project {
  display: flex;
  gap: 20px;
  margin-bottom: 30px;
}

.project .content {
  flex: 1;
  background: #2c1250;
  border-radius: 10px;
  padding: 20px;
  color: #ffffff;
}

.project .preview {
  flex: 1;
  background: #4f228d;
  border-radius: 10px;
}

/* Footer */
.footer {
  text-align: center;
  padding: 30px;
  background: #2c1250;
}

.footer p {
  margin: 10px 0;
  font-size: 1rem;
  color: #d9d9d9;
}

.footer .social-icons a {
  margin: 0 10px;
  color: #ffffff;
  text-decoration: none;
  font-size: 1.2rem;
}
</style>
