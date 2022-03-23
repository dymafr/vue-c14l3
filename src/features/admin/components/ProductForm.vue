<script setup lang="ts">
import { useForm, useField } from 'vee-validate';
import { z } from 'zod';
import { toFormValidator } from '@vee-validate/zod';
// import { onMounted, ref } from 'vue';
// const firstInput = ref<HTMLInputElement | null>(null);
// onMounted(() => {
//   firstInput.value?.focus();
// });

const required = { required_error: 'Veuillez renseigner ce champ' };
const validationSchema = toFormValidator(
  z.object({
    title: z
      .string(required)
      .min(1, { message: 'Le titre doit faire au moins 1 caractère' })
      .max(20, { message: 'Le titre doit faire moins de 20 caractères' }),
    image: z.string(required),
    price: z
      .number(required)
      .min(0, { message: 'Le prix doit être superieur à 0€' })
      .max(15000, { message: 'Le prix doit être inferieur à 150 00€' }),
    description: z
      .string(required)
      .min(10, { message: 'La description doit faire au moins 10 caractères' }),
    category: z.string(required),
  })
);
</script>

<template>
  <div class="card">
    <h1>Formulaire</h1>
  </div>
</template>

<style scoped lang="scss">
.card {
  width: 100%;
  max-width: 500px;
}
</style>
