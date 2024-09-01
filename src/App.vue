<script setup>
import AppHeader from './components/AppHeader.vue';
import UserList from './components/UserList.vue';
import RegisterUserArea from './components/RegisterUserArea.vue';

import { ref } from 'vue'

// const users = ref([
//   {
//     id: 1,
//     name: 'user 1',
//     email: 'mail_1@test.com',
//   },
//   {
//     id: 2,
//     name: 'user 2',
//     email: 'mail_2@test.com',
//   },
//   {
//     id: 3,
//     name: 'user 3',
//     email: 'mail_3@test.com',
//   },
// ]);
const users = ref([]);

const getUsers = async () => {
  const response = await fetch('http://localhost:3000/user');
  const data = await response.json();
  users.value = data;
};
getUsers();

const defaultUserInfo = {
  name: '',
  email: '',
};
const userInfo = ref(defaultUserInfo);
const isUserSelected = ref(false);

// リストからユーザーを選択した時の処理
const selectUser = (value) => {
  console.log(value);
  userInfo.value = value;
  console.log(userInfo);
  isUserSelected.value = true;
};

// ユーザー情報更新エリアで「ユーザー新規登録」ボタンをクリックしたときの処理
const clickUserRegistBtn = () => {
  userInfo.value = defaultUserInfo;
  isUserSelected.value = false;
};
</script>

<template>
  <v-app>
    <AppHeader title="User List" />
    <v-main>
      <RegisterUserArea :user="userInfo" :isUserSelected="isUserSelected" @click-user-regist-btn="clickUserRegistBtn" />
      <UserList :users="users" @select-user="selectUser" />
    </v-main>
  </v-app>
</template>

<style>
.v-application__wrap {
  all: unset;
}

main {
  padding-top: 64;
}
</style>
