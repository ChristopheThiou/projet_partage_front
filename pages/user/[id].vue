<script lang="ts" setup>
import { User } from "../../entities";

const route = useRoute();

const { data } = useFetch<User>('http://localhost:8000/api/user/id/' + route.params.id);

</script>

<template>
    <div v-if="data">
        <h3>{{ data.name }}</h3>
    <p>Address : {{ data.address }}</p>
    <p>List annonce : {{ data.listAnnonce }}</p>
    <p>List emprunt : {{ data.listEmprunt }}</p>
  </div>
</template>