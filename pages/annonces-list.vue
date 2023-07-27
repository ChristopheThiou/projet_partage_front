<script lang="ts" setup>
import { Annonce } from "entities";
const route = useRoute()

const { data, refresh } = useFetch<Annonce[]>("http://localhost:8000/api/annonce",{
  query:{search:route.query.search}
});



</script>

<template>
  <AnnoncesItem v-for="item of data" :annonce="item" />
</template>

<style scoped></style>
