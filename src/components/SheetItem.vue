<template>
  <v-sheet  :elevation="2" class="mb-4 mx-2">
    <v-sheet v-if="label" class="px-3 py-1 font-weight-bold border-b border-darker rounded-t">{{label}}:</v-sheet>
    <v-sheet class="pa-3 pt-6">
      <slot>{content}</slot>
    </v-sheet>
  </v-sheet>
</template>

<script setup>
const props = defineProps({
  label: String
})
</script>
