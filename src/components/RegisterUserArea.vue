<script setup>
import { computed } from 'vue'

const props = defineProps({
  user: {
    type: Object,
    required: true
  },
  isUserSelected: {
    type: Boolean,
    required: true
  }
});

const userInfo = computed(() => ({ ...props.user }));

const emit = defineEmits(['clickUserRegistBtn']);

// 「登録」ボタン押下
const clickRegistBtn = () => {
  console.log('「登録」ボタン押下');
};

// 「更新」ボタン押下
const clickUpdateBtn = () => {
  console.log('「更新」ボタン押下');
};

// 「削除」ボタン押下
const clickDeleteBtn = () => {
  console.log('「削除」ボタン押下');
};

// 「ユーザー新規登録」ボタン押下
const clickUserRegistBtn = () => {
  emit('clickUserRegistBtn');
};

</script>

<template>
  <v-layout>
    <v-card width="100vw">
      <v-card-item>
        <v-card-title v-if="props.isUserSelected">ユーザー情報更新</v-card-title>
        <v-card-title v-else>ユーザー情報新規登録</v-card-title>
      </v-card-item>
      <p>名前</p>
      <v-text-field label="name" v-model="userInfo.name"></v-text-field>
      <p>E-mail</p>
      <v-text-field label="Email address" placeholder="ex) hoge@fuga.com" type="email"
        v-model="userInfo.email"></v-text-field>
      <div v-if="props.isUserSelected">
        <v-btn @click="clickUpdateBtn">更新</v-btn>
        <v-btn @click="clickDeleteBtn">削除</v-btn>
        <v-btn @click="clickUserRegistBtn">ユーザー新規登録</v-btn>
      </div>
      <div v-else>
        <v-btn @click="clickRegistBtn">登録</v-btn>
      </div>
    </v-card>
    <div class="border border-b-lg" style="height: 64px; width: 64px;"></div>
  </v-layout>
</template>