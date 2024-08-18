<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer">
      <v-sheet class="pa-4" color="grey-lighten-4">
        <v-row align="center">
          <v-col>
            <div>Authenticated</div>
            <div style="color: gray; font-size: small;">Bearer</div>
          </v-col>
          <v-col class="text-right">
            <v-btn class="text-none" size="small" icon>
              <v-icon>mdi-key-variant</v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-sheet>

      <v-divider></v-divider>

      <v-list dense mandatory>
        <v-item-group v-model="selectedItem">
          <v-list-subheader>Getters</v-list-subheader>
          <v-list-item color="primary" v-for="(item, index) in mainItems" :key="index" :value="item.title"
            @click="navigate(item.title)">
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
          <v-divider style="margin-top: 10%; margin-bottom: 5%;"></v-divider>
          <v-list-item color="primary" v-for="(item, index) in settingsItems" :key="index" :value="item.title"
            @click="navigate(item.title)">
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar :elevation="0">
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-app-bar-title>MessageSyncer</v-app-bar-title>
    </v-app-bar>

    <v-main>
      {{ selectedItem }}
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue'

const drawer = ref(true)
const selectedItem = ref(null)
const mainItems = ref([
  { title: 'Getter#1' },
  { title: 'Getter#2' },
  { title: 'Getter#3' },
])
const settingsItems = ref([
  { title: 'Settings' },
  { title: 'About' },
])

function navigate(route) {
  selectedItem.value = route
  // Add navigation logic here, such as using Vue Router
  // router.push({ name: route });
}
</script>
