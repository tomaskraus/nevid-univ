<script setup>
const props = defineProps({
  item: Object,
})
</script>

<template>
  <div v-if="item.active">
    <v-icon color="success" icon="mdi-check-circle"></v-icon>
    <span class="text-success">&nbsp;{{ item.description }}</span>
  </div>
  <div v-else>
    <v-icon color="error" icon="mdi-close-circle"></v-icon>
    <span class="text-error">&nbsp;{{ item.description }}</span>
  </div>
</template>
