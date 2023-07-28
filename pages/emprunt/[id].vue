<script lang="ts" setup>
import { Emprunt } from "../../entities";

const route = useRoute();

const { data } = useFetch<Emprunt>(
  "http://localhost:8000/api/emprunt/" + route.params.id
);
</script>

<template>
  <div class="card mb-4" style="width: 18rem" v-if="data">
    <div class="card-body">
      <h5 class="card-title">{{ data.user.name }}</h5>
      <h6 class="card-subtitle mb-2 text-body-secondary">
        Accepted : {{ data.accepted }}
      </h6>
      <p class="card-text">Rendu : {{ data.rendu }}</p>
      <p class="card-text">Duration : {{ data.duration }}</p>
    </div>
  </div>
</template>
