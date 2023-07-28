<script lang="ts" setup>
import { User } from "../../entities";

const route = useRoute();

const { data } = useFetch<User>(
  "http://localhost:8000/api/user/id/" + route.params.id
);
</script>

<template>
  <div class="card mb-4" style="width: 18rem" v-if="data">
    <div class="card-body">
      <h5 class="card-title">{{ data.name }}</h5>
      <h6 class="card-subtitle mb-2 text-body-secondary">
        Address : {{ data.address }}
      </h6>
      <p class="card-text">List annonce : {{ data.listAnnonce }}</p>
      <p class="card-text">List emprunt : {{ data.listEmprunt }}</p>
    </div>
  </div>
</template>
