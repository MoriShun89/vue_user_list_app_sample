<script setup>
import { computed } from 'vue'

const props = defineProps({
  users: {
    type: Array,
    required: true
  }
});
const usersArray = computed(() => [...props.users]);

const emit = defineEmits(['selectUser']);

const selectUser = (value)=>{
  console.log(value.id);
  const selectedUser = value.id;
  emit('selectUser', selectedUser);
};
</script>

<template>
  <v-app>
    <v-main>
      <v-card class="mx-auto" width="100vw">
        <v-card-title>登録済みユーザー情報</v-card-title>
        <v-list v-on:click:select="selectUser">
          <v-list-item v-for="user in usersArray" :key="user.id" :value="user" color="primary">
            <v-list-item-title>{{ user.name }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-card>
    </v-main>
  </v-app>
</template>

<style>
.v-application__wrap {
  all: unset;
}
</style>
