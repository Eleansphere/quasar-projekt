<template>
  <q-number
        name="price"
        filled
        v-model="price"
        @update:price="onSubmit"
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
</template>
<script>
export default {
  setup() {

  },
}
</script>
