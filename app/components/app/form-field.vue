<script lang="ts" setup>
const props = defineProps<{
  label: string;
  name: string;
  type?: "text" | "textarea" | "number";
  error?: string;
  disabled?: boolean;
}>();
</script>

<template>
  <fieldset class="fieldset">
    <legend class="fieldset-legend">
      {{ props.label }}
    </legend>
    <Field
      :as="type === 'number' ? 'input' : type || 'input'"
      :name="props.name"
      :type="type || 'text'"
      class="w-full"
      :class="{
        'input-error': props.error,
        'input': !type || type === 'text' || type === 'number',
        'textarea': type === 'textarea',
      }"
      :disabled="disabled"
    />
    <p v-if="props.error" class="fieldset-label text-error">
      {{ props.error }}
    </p>
  </fieldset>
</template>
