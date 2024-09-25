<template>
  <div>
    <input-temp v-model="currentValue" label="Zadej čislo yo." />
    <pre>{{ currentValue }}</pre>
  </div>
</template>

<script setup lang="ts">
import inputTemp from 'src/components/input-temp.vue';
import { ref } from 'vue';

const currentValue = ref('');
</script>
