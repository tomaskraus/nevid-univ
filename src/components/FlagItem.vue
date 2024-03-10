<script setup>
const props = defineProps({
  description: String,
  active: Boolean,
})
</script>

<template>
  {{ `${active ? "v" : "x"} ${description}` }}
</template>
