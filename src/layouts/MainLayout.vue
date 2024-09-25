<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          <div class="absolute-center">
            <q-icon name="savings" />
            Input gather's App
          </div>
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      class="bg-primary"
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label class="text-white" header> Essential Links </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import EssentialLink, {
  EssentialLinkProps,
} from 'components/EssentialLink.vue';

defineOptions({
  name: 'MainLayout',
});

const linksList: EssentialLinkProps[] = [
  {
    title: 'Home',
    caption: 'ah home sweet home',
    icon: 'school',
    link: '/',
  },
  {
    title: 'Input',
    caption: 'go to input page',
    icon: 'code',
    link: '/input',
  },
  {
    title: 'Input2',
    caption: 'Better input',
    icon: 'code',
    link: '/input2',
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
