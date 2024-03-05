<script setup>
import { computed } from 'vue'

const props = defineProps({
  date: String
})


// const dateStr = 123
const dateStr = computed(() => {
  return new Date(props.date).toLocaleString('en-US', {
    weekday: 'short', // long, short, narrow
    // day: 'numeric', // numeric, 2-digit
    year: 'numeric', // numeric, 2-digit
    month: 'short', // numeric, 2-digit, long, short, narrow
    hour: 'numeric', // numeric, 2-digit
    minute: 'numeric', // numeric, 2-digit
    second: 'numeric', // numeric, 2-digit
  })
})

</script>


<template>
  {{ dateStr }}
</template>
