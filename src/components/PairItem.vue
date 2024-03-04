<template>
  <v-container class="pa-0 ma-0" style="max-width: 18em;">
        <v-row class="pa-0 ma-0 mb-0">
          <v-col cols="6" class="font-weight-bold pa-0 ma-0">
            {{ label }}:
          </v-col>
          <v-col cols="6" class="pa-0 ma-0">
            <slot></slot>
          </v-col>
        </v-row>
      </v-container>
</template>

<script setup>
const props = defineProps({
  label: String
})
</script>
