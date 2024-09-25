<template>
  <q-input
    v-model="formattedValue"
    label="Zadejte čísla"
    input-class="text-left"
    :rules="[(val) => val.length > 0 || 'Pole nebude prázdné!']"
  />
</template>

<script setup>
import { ref, watch } from 'vue';

// props pro hodnotu rodice
const props = defineProps({
  modelValue: {
    type: String,
    default: '',
  },
});

// emit props do rodice
const emit = defineEmits(['update:modelValue']);

const formattedValue = ref(props.modelValue);

// oddelam mezeru a pak zmenim , na tecku at to muzu poslat do rodice
const cleanValue = (value) => value.replace(/\s+/g, '').replace(',', '.');

// format cisla co posilam na horu, rozdelim na to pred teckou a po
const formatValue = (value) => {
  // carka oddelovac
  const parts = value.split('.');
  parts[0] = parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ' ');
  return parts.join(',');
};

// zmena v hodnote
watch(formattedValue, (newValue) => {
  // hotovy format pro rodice
  const clean = cleanValue(newValue);
  emit('update:modelValue', clean);

  formattedValue.value = formatValue(clean);
});
</script>
