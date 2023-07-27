<script lang="ts" setup>
import { Annonce } from "../../entities";

const route = useRoute();

const { data, refresh } = useFetch<Annonce>(
  "http://localhost:8000/api/annonce/id/" + route.params.id
);



async function removeAnnonce(annonce: Annonce) {
  await $fetch("http://localhost:8000/api/annonce/" + route.params.id, {
    method: "DELETE",
  });
  refresh();
}
</script>

<template>
  <div v-if="data">
    <h3>{{ data.name }}</h3>
    <p>Description : {{ data.description }}</p>
    <p>Comment : {{ data.comment }}</p>
    <p>Status : {{ data.status }}</p>
    <p>Type : {{ data.type }}</p>
    <form>
      <button @click="removeAnnonce(data)">Delete</button>
    </form>
  </div>
</template>
