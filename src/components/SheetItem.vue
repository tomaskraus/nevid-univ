<template>
  <v-sheet v-if="label" :elevation="2" class="px-3 py-1 font-weight-bold border-b border-darker rounded-t" color="grey-lighten-2">{{label}}:</v-sheet>
  <v-sheet  :elevation="2" class="pa-3 mb-4 ">
    <v-sheet class="pt-2">
      <slot>{content}</slot>
    </v-sheet>
  </v-sheet>
</template>

<script setup>
const props = defineProps({
  label: String
})
</script>
