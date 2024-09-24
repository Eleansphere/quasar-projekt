<template>
<div class="q-pa-md">
    <q-form @submit="onSubmit" class="q-gutter-md">
    <InputTemp />
    <DateInput />
      <div>
        <q-btn label="Submit" type="submit" color="primary" />
        <q-btn label="Reset" type="reset" color="secondary" />
      </div>
    </q-form>
  </div>
</template>

<script setup>
  import InputTemp from './InputTemp.vue';
  import DateInput from './DateInput.vue';
  import { ref } from 'vue';


  const submitResult = ref([]);

  function onSubmit(e) {
        const formData = new FormData(e.target);
        const data = [];

        for (const [name, value] of formData.entries()) {
          data.push({
            name,
            value,
          });
        }
        submitResult.value = data;
        console.log(submitResult.value);
      }


  // function onReset() {
  //     submitResult.value = '';
  //     price.value = '';
  //     date.value = '';
  //   }
</script>
