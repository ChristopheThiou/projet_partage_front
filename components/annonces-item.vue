<script lang="ts" setup>
import { Annonce } from "../entities";

defineProps<{
  annonce: Annonce;
}>();

</script>

<template>
  <div>
    <h3><NuxtLink :to="'/annonce/'+annonce._id">{{ annonce.name }}</NuxtLink></h3>
    <p>Description : {{ annonce.description }}</p>
    <p>Comment : {{ annonce.comment }}</p>
    <p>Status : {{ annonce.status }}</p>
    <p>Type : {{ annonce.type }}</p>
  </div>
</template>

<style scoped></style>