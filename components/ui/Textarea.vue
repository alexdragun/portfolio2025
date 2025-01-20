<script setup lang="ts">
interface Props {
  name: string;
  label: string;
  disabled?: boolean;
  placeholder?: string;
  type?: string;
  modelValue?: string;
  errorMessage?: string[];
  customErrors?: {
    type: string;
    message: string;
    valid: boolean;
  }[];
}

type EmitType = {
  (event: "update:modelValue", value: string): void;
};

const props = withDefaults(defineProps<Props>(), {
  type: "text",
});

const emit = defineEmits<EmitType>();

const name = toRef(props, "name");

const updateValue = (event: Event) => {
  let value = (event.target as HTMLInputElement).value;
  emit("update:modelValue", value);
};
</script>

<template>
  <div class="relative mb-8">
    <div
      class="form-group"
      :class="{ 'form-group--error': errorMessage && errorMessage.length }"
    >
      <textarea
        :type="type"
        :disabled="disabled"
        placeholder=" "
        :name="name"
        :id="name"
        spellcheck="false"
        :value="modelValue"
        @input="updateValue($event)"
      />
      <label :for="name">{{ label }}</label>
    </div>
    <span v-if="errorMessage?.[0]" class="error-message">
      {{ errorMessage?.[0] === "custom-error" ? "" : errorMessage?.[0] }}</span
    >
  </div>
</template>

<style lang="scss" scoped>
.form-group {
  @apply relative;
  &--error {
    textarea {
      border-color: #ef4444 !important;
    }
    label {
      color: #ef4444 !important;
    }
  }
}
.form-group textarea {
  transition: border-color 0.3s ease;
  @apply min-h-40 bg-transparent w-full px-6 py-6 border-b border-[var(--white)] text-base;
}
.form-group label {
  transition: 0.3s;
  @apply pointer-events-none absolute left-6 top-6 text-base text-[var(--white)];
}
.form-group textarea:focus {
  outline: none;
  @apply border-[var(--cyan)];
}
.form-group textarea:focus + label,
.form-group textarea:not(:placeholder-shown) + label {
  @apply text-[var(--white)] -translate-x-3 -translate-y-7;
}

.error-message {
  @apply absolute top-[calc(100%)] text-sm text-red-500 flex items-center;
}
</style>
