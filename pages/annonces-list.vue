<script lang="ts" setup>
import { Annonce } from "entities";

const { data, refresh } = useFetch<Annonce[]>("http://localhost:8000/api/annonce");
</script>

<template>
  <AnnoncesItem v-for="item of data" :annonce="item" />
</template>

<style scoped></style>
