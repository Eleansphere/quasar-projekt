<script setup lang="ts">
//q-number nepodporuje @input
// @update taky ale nejde :)) (aspon me :/)

import { ref, watch } from 'vue';

type DecimalFormat = 'cz' | 'eng';

const numberValue = ref<number | null>(null);

const props = defineProps<{
  decimalFormat: DecimalFormat;
  modelValue: string;
}>();

// emit modelValue parent
const emit = defineEmits(['update:modelValue']);

// zmena v hodnote (odeslani do rodice)
watch(numberValue, (newValue) => {
  const formattedString = newValue !== null ? newValue.toString() : '';
  emit('update:modelValue', formattedString);
});

//aktivni format
const decimalSeparator = ref<string>('');
watch(
  () => props.decimalFormat,
  (newLocale) => {
    decimalSeparator.value = newLocale === 'eng' ? '.' : ',';
  },
  { immediate: true }
);
</script>

<template>
  <q-number
    type="number"
    v-model="numberValue"
    label="Insert number yo."
    mask="number"
    input-class="text-left"
    :options="{
      prefix: '',
      suffix: '',
      separator: ' ',
      decimal: decimalSeparator,
      precision: 2,
      prefill: true,
      reverseFill: false,
      min: false,
      max: false,
      nullValue: '',
    }"
  />
</template>
