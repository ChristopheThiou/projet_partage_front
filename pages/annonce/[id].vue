<script lang="ts" setup>
import { Annonce } from "../../entities";

const route = useRoute();

const { data, refresh } = useFetch<Annonce>(
  "http://localhost:8000/api/annonce/id/" + route.params.id
);
async function updateAnnonce(annonce: Annonce) {
  await $fetch("http://localhost:8000/api/annonce/" + route.params.id, {
    method: "PATCH",
    body: annonce,
  });
  refresh();
}
function removeAnnonce() {
  $fetch("http://localhost:8000/api/annonce/" + route.params.id, {
    method: "DELETE",
  });
  refresh();
}

const emit = defineEmits(["submit"]);

function handleSubmite() {
  emit("submit", annonce.value);
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
  <div v-if="data">
    <h3>{{ data.name }}</h3>
    <p>Description : {{ data.description }}</p>
    <p>Comment : {{ data.comment }}</p>
    <p>Status : {{ data.status }}</p>
    <p>Type : {{ data.type }}</p>
    <form>
      <button @click="removeAnnonce()">Delete</button>
    </form>
    <form @submit.prevent="handleSubmite()">
      <p>
        <label for="name">Name : </label>
        <input
          type="text"
          v-model="annonce.name"
          placeholder="Type a name ..."
        />
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
        <input
          type="text"
          v-model="annonce.status"
          placeholder="Type a status ..."
        />
      </p>
      <p>
        <label for="type">Type : </label>
        <input
          type="text"
          v-model="annonce.type"
          placeholder="Type a type ..."
        />
      </p>
      <button @click="updateAnnonce(annonce)">Edit</button>
    </form>
  </div>
</template>
