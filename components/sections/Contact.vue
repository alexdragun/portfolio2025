<script setup lang="ts">
import Input from "@/components/ui/Input.vue";
import Textarea from "@/components/ui/Textarea.vue";
import { useValidation } from "vue3-form-validation";

const { $toast } = useNuxtApp();

const { form, validateFields, resetFields } = useValidation({
  name: {
    $value: "",
    $rules: [
      (name: string) => {
        if (!name) {
          return "Name is required";
        }
      },
    ],
  },
  email: {
    $value: "",
    $rules: [
      (email: string) => {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        if (!email) {
          return "Email is required";
        } else if (!emailRegex.test(email)) {
          return "Email format is not valid";
        }
      },
    ],
  },
  message: {
    $value: "",
    $rules: [
      (message: string) => {
        if (!message) {
          return "Message is required";
        }
      },
    ],
  },
});

const submitForm = async () => {
  await validateFields();
  await fetch("https://www.formbackend.com/f/47dcd0f20e746646", {
    method: "POST",
    headers: {
      Accept: "application/json",
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      name: form.name.$value,
      email: form.email.$value,
      message: form.message.$value,
    }),
  })
    .then((response) => {
      if (!response.status === 422) {
        throw new Error("Validation error");
      } else if (!response.ok) {
        throw new Error("Something went wrong");
      }
      $toast.success("Thank you for your message!");
      return response.json();
    })
    .catch((error) => {
      throw new Error(`Something went wrong: ${error}`);
    });
  await resetFields();
};
</script>

<template>
  <section class="container-custom" id="contactme">
    <div class="container-custom__inner">
      <h2 class="line mb-6">Contact me</h2>

      <form @submit.prevent="submitForm">
        <Input
          name="name"
          label="Name"
          :error-message="form.name.$errors"
          v-model="form.name.$value"
        />

        <Input
          name="email"
          label="Email"
          :error-message="form.email.$errors"
          v-model="form.email.$value"
        />

        <Textarea
          name="message"
          label="Message"
          :error-message="form.message.$errors"
          v-model="form.message.$value"
        />

        <button class="submit">Submit</button>
      </form>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.container-custom {
  &__inner {
    .form-item {
      label {
        @apply block;
      }
      input {
        @apply w-full;
      }
    }
    .submit {
      @apply block w-full max-w-64 ml-auto py-3 px-6 border border-[var(--cyan)] uppercase duration-300 hover:bg-[rgba(255,255,255,0.2)] cursor-pointer;
    }
  }
}
</style>
