<template>
  <v-container class="pa-0 ma-0" style="max-width: 24em;">
    <v-row align="center" class="pa-0 ma-0 mb-2">
      <v-col cols="4" class="font-weight-bold pa-0 ma-0">
        {{ capitalize(label) }}:
      </v-col>
      <v-col cols="8" class="pa-0 ma-0 w-auto">
        <slot></slot>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { capitalize } from 'vue';
const props = defineProps({
  label: String
})
</script>
