<template>
  <q-toolbar class="bg-orange-10 text-white">
    <q-btn flat round dense icon="music_note" />
    <q-toolbar-title> Pocket Music </q-toolbar-title>
    <!--<q-btn flat round dense icon="apps" class="q-mr-xs" />-->
    <q-btn flat round dense icon="more_vert" />
  </q-toolbar>
  <q-layout view="p">
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>
<script lang="ts"></script>
