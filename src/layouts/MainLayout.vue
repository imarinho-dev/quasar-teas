<template>
  <q-layout view="hHh lpR fFf">
    <q-header elevated class="bg-green-6 text-white">
      <q-toolbar>
        <q-toolbar-title class="uppercase">
          <q-avatar>
            <q-icon name="emoji_food_beverage" size="md" />
          </q-avatar>
          Chá
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-scroll-area
      visible
      :thumb-style="thumbStyle"
      :bar-style="barStyle"
      style="height: 100vh; max-width: 100%"
    >
      <q-page-container>
        <router-view />
      </q-page-container>
    </q-scroll-area>
  </q-layout>
</template>
<script setup>
const thumbStyle = {
  right: "4px",
  borderRadius: "5px",
  backgroundColor: "green",
  width: "5px",
  opacity: 0.75,
};

const barStyle = {
  right: "2px",
  borderRadius: "9px",
  backgroundColor: "green",
  width: "9px",
  opacity: 0.2,
};
</script>
