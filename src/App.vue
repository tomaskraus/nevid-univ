<template>
  <v-app class="rounded">
    <v-app-bar color="#4994EC" title="Application bar"></v-app-bar>

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
              <PairItem label="AuthInfo"><v-btn color="#4994EC" density="compact">show</v-btn></PairItem>
              <PairItem label="expires at">{{ Date.now() }}</PairItem>
            </SheetItem>
            <SheetItem label="def">
              <PairContainer>
                <PairItem label="name">Alice</PairItem>
                <PairItem label="occupation">clerk</PairItem>
              </PairContainer>
              <PairContainer>
                <PairItem label="name 2">Bob</PairItem>
                <PairItem label="occupation">worker</PairItem>
              </PairContainer>
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
</script>


<style>
html {
  line-height: 0.9;
  letter-spacing: -0.1;
  font-size: 0.8rem;
}
</style>
