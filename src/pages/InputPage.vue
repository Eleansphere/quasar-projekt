<!-- eslint-disable quotes -->
<script setup lang="ts">
import inputNumberTemp from 'src/components/input-number-temp.vue';
//komponent ma prop decimal-format, prijma hodnoty (cz || eng)

import { ref } from 'vue';

const currentValue = ref<string>('');
</script>

<template>
  <div>
    <inputNumberTemp decimal-format="cz" v-model="currentValue" />
    <pre>{{ currentValue }}</pre>
  </div>
</template>
