<template>
  <v-container class="pa-0 ma-0" style="max-width: 24em;">
    <v-row :align="verticalAlign" class="pa-0 ma-0 mb-2">
      <v-col cols="5" class="font-weight-bold pa-0 ma-0">
        <v-icon v-if="prependIcon" :color="iconColor" :icon="prependIcon"></v-icon>
        {{ capitalize(label) }}:
      </v-col>
      <v-col cols="7" class="pa-0 ma-0 w-auto">
        <slot></slot>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { capitalize, computed } from 'vue';
const props = defineProps({
  label: String,
  prependIcon: String, // icon name, such as "mdi-check". Just type a nonexistent icon name to create an empty space
  iconColor: String,
  align: String   //"center" | "end" | "start" | "stretch" | "baseline"
})

const verticalAlign = computed(() => props.align || "center")
</script>
