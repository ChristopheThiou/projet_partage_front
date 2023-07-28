<script lang="ts" setup>
import { Annonce } from "../entities";

const { refresh } = useFetch<Annonce[]>("http://localhost:8000/api/annonce");

async function postAnnonce() {
  await $fetch("http://localhost:8000/api/annonce", {
    method: "POST",
    body: annonce.value,
  });
  refresh();
}

const annonce = ref<Annonce>({
  name: "",
  description: "",
  comment: "",
  status: "",
  type: "",
});
</script>

<template>
  <form @submit.prevent="postAnnonce()">
    <div class="mb-3">
      <label for="name" class="form-label">Name : </label>
      <input
        type="text"
        v-model="annonce.name"
        class="form-control"
        id="name"
        aria-describedby="name"
      />
    </div>
    <div class="mb-3">
      <label for="description" class="form-label">Description : </label>
      <textarea
        type="text"
        v-model="annonce.description"
        class="form-control"
        id="description"
      />
    </div>
    <div class="mb-3">
      <label for="comment" class="form-label">Comment : </label>
      <textarea
        type="text"
        v-model="annonce.comment"
        class="form-control"
        id="comment"
      />
    </div>
    <div class="mb-3">
      <label for="status" class="form-label">Status : </label>
      <input
        type="text"
        v-model="annonce.status"
        class="form-control"
        id="status"
        aria-describedby="status"
      />
    </div>
    <div class="mb-3">
      <label for="type" class="form-label">Type : </label>
      <input
        type="text"
        v-model="annonce.type"
        class="form-control"
        id="type"
        aria-describedby="type"
      />
    </div>
    <button type="submit" class="btn btn-primary">Add</button>
  </form>
</template>

<style scoped></style>
