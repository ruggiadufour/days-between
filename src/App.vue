<script setup lang="ts">
import { ref, computed } from 'vue';
import { differenceInDays } from 'date-fns';

const date1 = ref(new Date());
const date2 = ref(new Date());

const days = computed(() => {
  if (!date1.value || !date2.value) return 0;
  return differenceInDays(date2.value, date1.value);
});

const months = computed(() => {
  if (!days.value) return 0;
  const averageMonth = 365 / 12;
  return (days.value / averageMonth).toFixed(2);
});

const years = computed(() => {
  if (!months.value) return 0;
  return (months.value / 12).toFixed(2);
});
</script>

<template>
  <input v-model="date1" type="date" />
  <input v-model="date2" type="date" />
  <br />
  Days: {{ days }}
  <br />
  Months: {{ months }}
  <br />
  Years: {{ years }}
</template>

<style scoped></style>
