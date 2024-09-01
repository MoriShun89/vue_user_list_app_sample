<script setup>
defineProps({
  title: {
    type: String,
    required: true
  }
})
</script>

<template>
  <v-app-bar :elevation="1">
    <template v-slot:prepend>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
    </template>
    <v-app-bar-title>{{ title }}</v-app-bar-title>
  </v-app-bar>
</template>

<style>
.v-application__wrap {
  all: unset;
}
</style>
