<template>
  <v-sheet v-if="label" :elevation="2" class="px-3 py-2 font-weight-bold border-b border-darker rounded-t"
    color="grey-lighten-3">{{ capitalize(label) }}:</v-sheet>
  <v-sheet :elevation="2" class="pa-3 mb-6">
    <v-sheet class="pt-2">
      <slot>{content}</slot>
    </v-sheet>
  </v-sheet>
</template>

<script setup>
import { capitalize } from 'vue';
const props = defineProps({
  label: String
})
</script>
