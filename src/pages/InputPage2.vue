<template>
  <div>
    <input-temp v-model.coma.trim="currentValue" label="Zadej čislo yo." />
    <pre>{{ inputNumbers }}</pre>
  </div>
</template>

<script setup lang="ts">
import inputTemp from 'src/components/input-temp.vue';
import { computed, ref } from 'vue';

const currentValue = ref('');

const inputNumbers = computed(() => {
  return new Intl.NumberFormat('cz').format(
    Number(currentValue.value.replace(/\s+/g, ''))
  );
});
</script>
