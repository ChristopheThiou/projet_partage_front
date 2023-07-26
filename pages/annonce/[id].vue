<script lang="ts" setup>
import { Annonce } from "../../entities";

const route = useRoute();

const { data } = useFetch<Annonce>('http://localhost:8000/api/annonce/id/' + route.params.id);

</script>

<template>
    <div v-if="data">
        <h3>{{ data.name }}</h3>
    <p>Description : {{ data.description }}</p>
    <p>Comment : {{ data.comment }}</p>
    <p>Disponible : {{ data.disponible }}</p>
    <p>Status : {{ data.status }}</p>
    <p>Type : {{ data.type }}</p>
  </div>
</template>