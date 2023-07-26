<script lang="ts" setup>
import { Emprunt } from "../entities";

defineProps<{
  emprunt: Emprunt;
}>();
</script>

<template>
  <div>
    <h3><NuxtLink :to="'/emprunt/'+emprunt._id">{{ emprunt.user.name }}</NuxtLink></h3>
    <p>Accepted : {{ emprunt.accepted }}</p>
    <p>Rendu : {{ emprunt.rendu }}</p>
    <p>Duration : {{ emprunt.duration }}</p>
  </div>
</template>

<style scoped></style>