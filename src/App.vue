<script setup>
import { ref } from 'vue'

const uData = ref({})

import data from '../public/domain'
uData.value = data;

</script>


<template>
  <v-app class="rounded">
    <v-app-bar color="primary">
      <v-app-bar-nav-icon prepend-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Ferda</v-toolbar-title>
    </v-app-bar>

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
              <PairItem label="AuthInfo"><v-btn color="primary" density="compact">show</v-btn></PairItem>
              <PairItem label="expires at">
                <DateItem :date="uData.expires_at" />
              </PairItem>
            </SheetItem>

            <SheetItem label="events">
              <PairContainer>
                <PairItem label="create date">
                  <DateItem :date="uData.events.registered?.timestamp" />
                </PairItem>
                <PairItem v-if="uData.events.registered?.timestamp" label="registrar">
                  <span class="text-primary">{{ uData.events.registered?.registrar_handle }}</span></PairItem>
              </PairContainer>
              <PairContainer>
                <PairItem label="update date">
                  <DateItem :date="uData.events.updated?.timestamp" />
                </PairItem>
                <PairItem v-if="uData.events.updated?.timestamp" label="registrar">
                  <span class="text-primary">{{ uData.events.updated?.registrar_handle }}</span>
                </PairItem>
              </PairContainer>
              <PairContainer>
                <PairItem label="transfer date">
                  <DateItem :date="uData.events.transferred?.timestamp" />
                </PairItem>
                <PairItem v-if="uData.events.transferred?.timestamp" label="registrar">
                  <span class="text-primary">{{ uData.events.transferred?.registrar_handle }}</span></PairItem>
              </PairContainer>
              <PairContainer>
                <PairItem label="delete date">
                  <DateItem :date="uData.events.unregistered?.timestamp" />
                </PairItem>
                <PairItem v-if="uData.events.unregistered?.timestamp" label="registrar">
                  <span class="text-primary">{{ uData.events.unregistered?.registrar_handle }}</span></PairItem>
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


<style>
html {
  line-height: 0.9;
  letter-spacing: -0.1;
  font-size: 0.8rem;
}
</style>
