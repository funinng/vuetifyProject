<template>
  <v-app id="inspire" :theme="themeInfo">
    <v-navigation-drawer disable-resize-watcher v-model="drawer">
      <DrawerHeader />
    </v-navigation-drawer>

    <v-app-bar>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-main>
      <v-container class="container" fluid>
        <router-view v-slot="{ Component }">
  <transition name="fade">
    <component :is="Component" />
  </transition>
</router-view>
      </v-container>
    </v-main>
  </v-app>
</template>
<script lang="ts" setup>
import DrawerHeader from "./DrawerHeader.vue";
import { ref } from "vue";

const themeInfo = ref("light");
// const themeMedia = window.matchMedia("(prefers-color-scheme: light)");
// themeMedia.matches ? (themeInfo.value = "light") : (themeInfo.value = "dark");

const drawer = ref(false);
</script>
<style lang="scss">
#inspire {
  height: 100%;
  .container {
    height: 100%;
  }
}
</style>
