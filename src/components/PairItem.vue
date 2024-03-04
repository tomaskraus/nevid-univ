<template>
  <v-container class="pa-0 ma-0 w-100">
        <v-row>
          <v-col cols="6" xs="6" class="font-weight-bold py-0">
            {{ label }}:
          </v-col>
          <v-col cols="6" xs="6" class="pt-0 pb-3">
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
