<template>
  <v-sheet  :elevation="2" class="my-3 "  >
    <v-sheet class="px-3 py-1 font-weight-bold" color="grey-lighten-2">{{label || '{Label}'}}:</v-sheet>
    <v-sheet class="pa-3">
      <slot>{content}</slot>
    </v-sheet>
  </v-sheet>
</template>

<script setup>
const props = defineProps({
  label: String
})
</script>
