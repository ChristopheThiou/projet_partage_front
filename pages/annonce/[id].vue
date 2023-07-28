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
  <div class="card mb-4" style="width: 18rem" v-if="data">
    <div class="card-body">
      <h5 class="card-title">{{ data.name }}</h5>
      <h6 class="card-subtitle mb-2 text-body-secondary">
        Description : {{ data.description }}
      </h6>
      <p class="card-text">Comment : {{ data.comment }}</p>
      <p class="card-text">Status : {{ data.status }}</p>
      <p class="card-text">Type : {{ data.type }}</p>
      <form>
        <button class="btn btn-danger" @click="removeAnnonce()">Delete</button>
      </form>
    </div>
  </div>

  <form @submit.prevent="handleSubmite()">
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
    <button
      @click="updateAnnonce(annonce)"
      type="submit"
      class="btn btn-primary"
    >
      Edit
    </button>
  </form>
</template>
