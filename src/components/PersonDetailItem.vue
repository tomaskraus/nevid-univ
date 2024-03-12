<script setup>
const props = defineProps({
  person: Object,
})

function getIcon(publishFlag) {
  return publishFlag ? 'mdi-eye' : 'mdi-eye-off'
}

function getColor(publishFlag) {
  return publishFlag ? 'success' : 'error'
}
</script>

<template>
  <PairItem label="handle" prepend-icon="-" iconColor="success"><span class="text-primary">{{ person.handle
  }}</span></PairItem>

  <PairItem label="organization" :prepend-icon="getIcon(person.publish.organization)"
    :iconColor="getColor(person.publish.organization)">
    {{ person.organization }}
  </PairItem>

  <PairItem label="name" :prepend-icon="getIcon(person.publish.name)" :iconColor="getColor(person.publish.name)">
    {{ person.name }}</PairItem>
</template>
