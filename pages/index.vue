<script lang="ts" setup>
import { User } from "entities";

const { data, refresh } = useFetch<User[]>("http://localhost:8000/api/user");

async function postUser(user:User){
  await $fetch('http://localhost:8000/api/user', {
    method: 'POST',
    body: user
  })
  refresh();
}
</script>

<template>
  <FormUser @submit="postUser($event)"/>
  <UserItem v-for="item of data" :user="item" />
</template>

<style scoped></style>