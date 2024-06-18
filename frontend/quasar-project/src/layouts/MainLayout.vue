<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-light-blue text-white" height-hint="98">
      <q-toolbar>
        <q-btn
          href="/"
          label="Odjava"
          color="white"
          flat
          icon="directions"
        />
        <q-toolbar-title class="text-weight-medium text-center text-h4">
          Evidencija stručnog usavršavanja
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Izbornik </q-item-label>

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";
const linksList = [
  {
    title: "Profesori",
    icon: "human",
    link: "#/profesoriPage",
    target: "_self",
  },
  {
    title: "Stručno usavršavanje",
    icon: "document",
    link: "#/usavrsavanje",
    target: "_self",
  },
  {
    title: "Radovi",
    icon: "document",
    link: "#/radovi",
    target: "_self",
  },
  {
    title: "Erasmus",
    icon: "document",
    link: "#/erasmus",
    target: "_self",
  },
  {
    title: "Kategorizacija rada",
    icon: "document",
    link: "#/vrsteMobilnosti",
    target: "_self",
  }
];
export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>

<style>
.bg-light-blue {
  background-color: #add8e6;
}
</style>
