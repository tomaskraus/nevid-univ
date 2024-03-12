<script setup>
import { ref, computed } from 'vue'
import { useDisplay } from 'vuetify'
const { mdAndUp } = useDisplay()

const uData = ref(null)
const detail = ref(false)


import data from '../public/domain'
uData.value = data;


const stateFlags = computed(() => {
  if (!uData.value) {
    return []
  }
  if (detail.value) {
    return uData.value.state_flags.flags
  }
  return uData.value.state_flags.flags.filter((f) => f.active)
})

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
        <h2>neviditelna-univerzita.cz</h2>
        <v-switch label="Verbose view" v-model="detail" color="primary"></v-switch>
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
                  <span class="text-primary">{{ uData.events.registered?.registrar_handle }}</span>
                </PairItem>
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
                  <span class="text-primary">{{ uData.events.transferred?.registrar_handle }}</span>
                </PairItem>
              </PairContainer>
              <PairContainer>
                <PairItem label="delete date">
                  <DateItem :date="uData.events.unregistered?.timestamp" />
                </PairItem>
                <PairItem v-if="uData.events.unregistered?.timestamp" label="registrar">
                  <span class="text-primary">{{ uData.events.unregistered?.registrar_handle }}</span>
                </PairItem>
              </PairContainer>
            </SheetItem>

            <SheetItem label="state flags">
              <v-sheet class="d-flex flex-column flex-wrap overflow-hidden" :max-height="mdAndUp ? 300 : 'none'">
                <div class="pb-2 mr-2" v-for="f in stateFlags">
                  <FlagItem :item="f" />
                </div>
              </v-sheet>
            </SheetItem>

          </v-col>
          <v-col cols="12" lg="4">
            <SheetItem label="owner">
              <PersonDetailItem :person="uData.owner"></PersonDetailItem>
            </SheetItem>

            <v-container v-if="detail" class="ma-0 pa-0">
              <SheetItem v-for="ac in uData.administrative_contacts" label="administrative contact">
                <PersonDetailItem :person="ac"></PersonDetailItem>
              </SheetItem>
            </v-container>
            <v-container v-else class="ma-0 pa-0">
              <SheetItem label="administrative contacts">
                <PairItem v-for="ac in uData.administrative_contacts" :label="ac.name">
                  <span class="text-primary">{{ ac.handle }}</span>
                </PairItem>
              </SheetItem>
            </v-container>

            <SheetItem label="NSSet">
              <PairItem label="handle"><span class="text-primary">{{ uData.nsset.handle }}</span></PairItem>
              <PairItem label="registrar"><span class="text-primary">{{ uData.nsset.registrar }}</span></PairItem>
              <PairItem label="DNS">
                <ul>
                  <li class="my-list-item-simple pb-1" v-for="d in uData.nsset.dns">
                    {{ `${d.name} (${d.ip_address})` }}
                  </li>
                </ul>
              </PairItem>
            </SheetItem>

            <SheetItem label="KeySet">
              <PairItem label="handle"><span class="text-primary">{{ uData.keyset.handle }}</span></PairItem>
              <PairItem label="registrar"><span class="text-primary">{{ uData.keyset.registrar }}</span></PairItem>
              <PairItem label="DNS Keys">
                <ul>
                  <li class="my-list-item-simple pb-2 my-no-overflow" v-for="k in uData.keyset.dns_keys">
                    {{ k }}
                  </li>
                </ul>
              </PairItem>
            </SheetItem>

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

.my-list-item-simple {
  list-style-type: none;
}

.my-no-overflow {
  /* white-space: nowrap; */
  /* overflow: hidden; */
  /* text-overflow: ellipsis; */
  word-wrap: break-word;
}
</style>
