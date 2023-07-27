<script lang="ts" setup>
import { Annonce } from "../entities";

defineProps<{
  annonce: Annonce;
}>();
</script>

<template>
  <div class="card mb-4" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title">{{ annonce.name }}</h5>
      <h6 class="card-subtitle mb-2 text-body-secondary">
        Description : {{ annonce.description }}
      </h6>
      <p class="card-text">Comment : {{ annonce.comment }}</p>
      <p class="card-text">Status : {{ annonce.status }}</p>
      <p class="card-text">Type : {{ annonce.type }}</p>
      <NuxtLink :to="'/annonce/' + annonce._id"
        ><button class="btn btn-primary">Details</button></NuxtLink
      >
    </div>
  </div>
</template>

<style scoped></style>
