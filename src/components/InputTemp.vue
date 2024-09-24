<template>
  <div>
    <q-input
        type="number"
        name="price"
        filled
        v-model.number="price"
        label="Insert number"
        input-class="text-left"
      />
      <p>{{ inputNumbers }}</p>
  </div>
</template>
<script setup lang="ts">
import { ref, computed } from 'vue';



  const price = ref();
  const inputNumbers = computed(() =>{
    return new Intl.NumberFormat('cz').format(price.value)
  });
</script>
