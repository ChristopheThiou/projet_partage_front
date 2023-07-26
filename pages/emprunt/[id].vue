<script lang="ts" setup>
import { Emprunt } from "../../entities";

const route = useRoute();

const { data } = useFetch<Emprunt>(
  "http://localhost:8000/api/emprunt/" + route.params.id
);
</script>

<template>
  <div v-if="data">
    <h3>{{ data.user.name }}</h3>
    <p>Accepted : {{ data.accepted }}</p>
    <p>Rendu : {{ data.rendu }}</p>
    <p>Duration : {{ data.duration }}</p>
  </div>
</template>
