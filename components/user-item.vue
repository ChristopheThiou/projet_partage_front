<script lang="ts" setup>
import { User } from "../entities";

defineProps<{
  user: User;
}>();
</script>

<template>
  <div class="card mb-4" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title">{{ user.name }}</h5>
      <h6 class="card-subtitle mb-2 text-body-secondary">
        Address : {{ user.address }}
      </h6>
      <p class="card-text">List annonce : {{ user.listAnnonce }}</p>
      <p class="card-text">List emprunt : {{ user.listEmprunt }}</p>
      <NuxtLink :to="'/user/' + user._id"
        ><button class="btn btn-primary">Details</button></NuxtLink>
    </div>
  </div>
</template>

<style scoped></style>
