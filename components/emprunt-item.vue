<script lang="ts" setup>
import { Emprunt } from "../entities";

defineProps<{
  emprunt: Emprunt;
}>();
</script>

<template>
  <div class="card mb-4" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title">{{ emprunt.user.name }}</h5>
      <h6 class="card-subtitle mb-2 text-body-secondary">
        Accepted : {{ emprunt.accepted }}
      </h6>
      <p class="card-text">Rendu : {{ emprunt.rendu }}</p>
      <p class="card-text">Duration : {{ emprunt.duration }}</p>
      <NuxtLink :to="'/emprunt/' + emprunt._id"
        ><button class="btn btn-primary">Details</button></NuxtLink
      >
    </div>
  </div>
</template>

<style scoped></style>