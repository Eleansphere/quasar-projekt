<template>
  <div class="q-pa-md" style="max-width: 300px">
    <q-input name="dateInput" filled v-model="dateRef" mask="##/##/####" :rules="[v => /^[0-3]\d\/[0-1]\d\/-?[\d]+$/
      .test(v) ||'Please enter valid date']">
      <template v-slot:append>
        <q-icon name="event" class="cursor-pointer">
          <q-popup-proxy cover transition-show="scale" transition-hide="scale">
            <q-date v-model="dateRef" mask="DD/MM/YYYY">
              <div class="row items-center justify-end">
                <q-btn v-close-popup label="Close" color="primary" flat />
              </div>
            </q-date>
          </q-popup-proxy>
        </q-icon>
      </template>
    </q-input>
                  <pre>{{ dateRef }}</pre>
  </div>
</template>


<script setup lang="ts">
import { ref } from 'vue'

const dateRef = ref('02/12/1992');
</script>
