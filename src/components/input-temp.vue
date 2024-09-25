<template>
  <q-input
    name="price"
    filled
    v-model="model"
    label="Insert number"
    input-class="text-left"
  />
</template>

<script setup lang="ts">
//2w binding pomoci component modelu
const [model, modifiers] = defineModel({
  set(value: string) {
    if (modifiers.coma) {
      return value.replace(',', '.');
    }
    return;
  },
  default: '',
});
</script>
