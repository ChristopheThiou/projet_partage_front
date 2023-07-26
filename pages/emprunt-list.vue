<script lang="ts" setup>
import { Emprunt } from "entities";

const { data, refresh } = useFetch<Emprunt[]>("http://localhost:8000/api/emprunt");
</script>

<template>
  <EmpruntItem v-for="item of data" :emprunt="item" />
</template>

<style scoped></style>