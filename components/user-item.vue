<script lang="ts" setup>
import { User } from "../entities";

defineProps<{
  user: User;
}>();
</script>

<template>
  <div>
    <h3><NuxtLink :to="'/user/'+user._id">{{ user.name }}</NuxtLink></h3>
    <p>Address : {{ user.address }}</p>
    <p>List annonce : {{ user.listAnnonce }}</p>
    <p>List emprunt : {{ user.listEmprunt }}</p>
  </div>
</template>

<style scoped></style>