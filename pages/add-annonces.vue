<script lang="ts" setup>
import { Annonce } from "../entities";

const { refresh } = useFetch<Annonce[]>("http://localhost:8000/api/annonce");

async function postAnnonce(){
  await $fetch('http://localhost:8000/api/annonce', {
    method: 'POST',
    body: annonce.value
  })
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
    <p>
      <label for="name">Name : </label>
      <input type="text" v-model="annonce.name" placeholder="Type a name ..." />
    </p>
    <p>
      <label for="description">Description : </label>
      <textarea
        type="text"
        v-model="annonce.description"
        placeholder="Type a description ..."
      />
    </p>
    <p>
      <label for="comment">Comment : </label>
      <textarea
        type="text"
        v-model="annonce.comment"
        placeholder="Type a comment ..."
      />
    </p>
    <p>
      <label for="status">Status : </label>
      <input type="text" v-model="annonce.status" placeholder="Type a status ..." />
    </p>
    <p>
      <label for="type">Type : </label>
      <input type="text" v-model="annonce.type" placeholder="Type a type ..." />
    </p>
    <button>Add</button>
  </form>
</template>

<style scoped></style>
