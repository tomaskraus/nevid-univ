<template>
  <v-layout class="rounded rounded-md">
    <v-app-bar title="Application bar"></v-app-bar>

    <v-navigation-drawer>
      <v-list>
        <v-list-item title="Navigation drawer"></v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main class="d-flex align-center justify-center" style="min-height: 300px;">

      <v-container>
        <v-row justify="space-around">
          <v-col cols="12" md="6">
            <SheetItem>Hello!</SheetItem>
            <SheetItem label="def">Hello!</SheetItem>
            <SheetItem label="3rd lbl">Hello!</SheetItem>
          </v-col>
          <v-col cols="12" md="6">
            <SheetItem label="common">World</SheetItem>
            <SheetItem></SheetItem>
          </v-col>
        </v-row>
      </v-container>


    </v-main>
  </v-layout>
</template>

<script setup>
import HelloWorld from './components/HelloWorld.vue';


const elevations = [0, 4, 8, 12, 16, 20]


//
</script>
