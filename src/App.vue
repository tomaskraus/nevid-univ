<template>
  <v-app class="rounded">
    <v-app-bar title="Application bar"></v-app-bar>

    <v-navigation-drawer mobile-breakpoint="sm">
      <v-list>
        <v-list-item title="Navigation drawer"></v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main class="align-center justify-center" style="min-height: 300px;">

      <v-container style="max-width: 1600px;">
        <v-row>
          <v-col cols="12" lg="8">
            <SheetItem>
              <PairItem label="AuthInfo">{{ Date.now() }}</PairItem>
              <PairItem label="expires at"><v-btn density="compact">show</v-btn></PairItem>
            </SheetItem>
            <SheetItem label="def">
              <v-container class="ma-0 pa-0 pb-1 d-flex flex-wrap">
                    <PairItem label="name">Alice</PairItem>
                    <PairItem label="occupation">clerk</PairItem>
              </v-container>
              <v-container class="ma-0 pa-0 pb-1 d-flex flex-wrap">
                <PairItem label="name 2">Bob</PairItem>
                <PairItem label="occupation">worker</PairItem>
              </v-container>

            </SheetItem>
            <SheetItem label="3rd lbl">Hello!</SheetItem>
          </v-col>
          <v-col cols="12" lg="4">
            <SheetItem label="common">
              <PairItem label="name 2">Bob</PairItem>
            </SheetItem>
            <SheetItem></SheetItem>
          </v-col>
        </v-row>
      </v-container>


    </v-main>
  </v-app>
</template>

<script setup>
import PairItem from './components/PairItem.vue';


</script>
