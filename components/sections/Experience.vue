<script setup lang="ts">
import moment from "moment";

const experiences = ref([
  {
    title: "Full-stack Developer",
    company: "CONET Hrvatska",
    companyImage:
      "https://media.licdn.com/dms/image/v2/C4E0BAQH-VR5O5jwfjQ/company-logo_200_200/company-logo_200_200/0/1630648060321?e=1745452800&v=beta&t=MnnbZtuknrpWrwpw70x5JmBQRdKus_IiaRXDZxjA84Q",
    startDate: new Date("11/15/2023"),
    endDate: null,
    description:
      "• Implement advanced features, reusable components, and global state management using Pinia <br>• Reviewing code to ensure it meets the projects coding standards<br>• Ensure responsiveness and device compatibility<br>• Enhance application performance and security<br>• Stay current with latest frontend technologies",
  },
  {
    title: "Senior Frontend Developer",
    company: "Barrage",
    companyImage:
      "https://media.licdn.com/dms/image/v2/C560BAQEPISvUtxzB6Q/company-logo_200_200/company-logo_200_200/0/1630571816450/barragehq_logo?e=1745452800&v=beta&t=nj5NXrXITk_EFlzWH88hXhLlhBiJ9Mpwsug-5emS1wE",
    startDate: new Date("09/01/2020"),
    endDate: new Date("10/01/2023"),
    description:
      "• Develop web applications using Vue and Nuxt<br>• Implement advanced features, reusable components, and global state management using Vuex/Pinia<br>• Reviewing code to ensure it meets the projects coding standards<br>• Collaborate across different teams to develop intuitive and user-friendly interfaces<br>• Ensure responsiveness and device compatibility<br>• Enhance application performance<br>• Stay current with latest frontend technologies<br>• Mentoring junior developers",
  },
  {
    title: "Junior Frontend Developer",
    company: "Gauss Development",
    companyImage:
      "https://media.licdn.com/dms/image/v2/D4D0BAQGewE5La8K-Pg/company-logo_200_200/company-logo_200_200/0/1708505336589/gauss_development_logo?e=1745452800&v=beta&t=wZeOxtTqV9NTJtbWbhrSHyG7FPSayL0tCv3ghNfOxhs",
    startDate: new Date("10/01/2018"),
    endDate: new Date("09/01/2020"),
    description:
      "• Collaborate with the design team to develop intuitive and user-friendly interfaces<br>• Write clean and efficient code using HTML, CSS, JavaScript and other frontend technologies<br>• Ensure cross-browser compatibility and responsiveness of web applications<br>• Optimize web application performance for maximum speed and scalability<br>• Troubleshoot and debug frontend issues as they arise<br>• Stay up-to-date with emerging trends and technologies in frontend development",
  },
]);

const calculateDuration = (start: string | Date, end: string | Date | null) => {
  const startDate = moment(start, "YYYY-MM-DD");
  const endDate = moment(end || new Date(), "YYYY-MM-DD");

  // Calculate the difference
  let years = endDate.diff(startDate, "years"); // Full years difference
  startDate.add(years, "years"); // Adjust the start date by adding full years
  let months = endDate.diff(startDate, "months") + 1; // Remaining months

  if (months >= 12) {
    years += Math.floor(months / 12);
    months = months % 12;
  }

  // Format the output
  const formattedDuration = `${years} yr${years !== 1 ? "s" : ""}${
    months > 0 ? ` ${months} mo${months !== 1 ? "s" : ""}` : ""
  }`;

  return formattedDuration;
};
</script>

<template>
  <section class="container-custom" id="experience">
    <div class="container-custom__inner">
      <h2 class="text-4xl line mb-6">Experience</h2>
      <div class="mt-16">
        <div
          class="experience"
          v-for="(experience, index) in experiences"
          :key="index"
        >
          <img :src="experience.companyImage" :alt="experience.company" />
          <div>
            <p class="mb-1">{{ experience.title }}</p>
            <h3 class="text-xl">{{ experience.company }}</h3>
            <p class="opacity-60 mb-6">
              {{ moment(experience.startDate).format("MMM YYYY") }} -
              {{
                experience.endDate
                  ? moment(experience.endDate).format("MMM YYYY")
                  : "Present"
              }}
              •
              {{ calculateDuration(experience.startDate, experience.endDate) }}
            </p>
            <p v-html="experience.description" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.container-custom {
  &__inner {
    .experience {
      @apply flex gap-4 md:gap-8 pt-8 md:pt-16 pb-8 md:pb-16 mb-[14px] relative last:mb-0;
      &:before {
        content: "";
        @apply block w-[3px] bg-[var(--cyan)] absolute top-0 left-[31px] md:left-[63px] bottom-0 last:bottom-[90%] md:last:bottom-[80%];
      }
      &:after {
        content: "○";
        @apply text-4xl absolute -top-[28px] left-[22px] md:left-[54px];
      }
      img {
        @apply w-16 h-16 md:w-32 md:h-32 rounded-full relative z-10;
      }
    }
  }
}
</style>
