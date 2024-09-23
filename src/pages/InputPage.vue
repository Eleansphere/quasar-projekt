<template>
  <div class="q-pa-md">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        type="number"
        name="price"
        filled
        v-model.number="price"
        :options="{
          prefix: '',
          suffix: '',
          separator: ' ',
          decimal: '.',
          precision: 2,
          prefill: false,
          reverseFill: false,
          min: false,
          max: false,
          nullValue: '',
        }"
        label="Insert number"
        :rules="[(val) => !!val || 'Field is required!']"
        input-class="text-left"
      />
      <div class="q-pa-md" style="max-width: 300px">
    <q-input filled name="dateInput" v-model="date" mask="date" :rules="['date']">
      <template v-slot:append>
        <q-icon name="event" class="cursor-pointer">
          <q-popup-proxy cover transition-show="scale" transition-hide="scale">
            <q-date v-model="date">
              <div class="row items-center justify-end">
                <q-btn v-close-popup label="Close" color="primary" flat />
              </div>
            </q-date>
          </q-popup-proxy>
        </q-icon>
      </template>
    </q-input>
  </div>

      <div>
        <q-btn label="Submit" type="submit" color="primary" />
        <q-btn label="Reset" type="reset" color="secondary" />
      </div>
    </q-form>

    <p>Your inserted number is: {{ new Intl.NumberFormat('cz').format(price) }}</p>
    <p>Date is: {{ date }}</p>
  </div>
</template>

<script>

import { ref } from 'vue';

export default {
  setup() {
    const submitResult = ref([]);
    const price = ref('');
    const date = ref('')
    return {
      price,
      submitResult,
      date,

      onSubmit(e) {
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
      },
      onReset() {
        submitResult.value = '';
        price.value = '';
        date.value = '';
      },
    };
  },
  components:{

  },
};
</script>

