<script lang="ts" setup>
import { User } from "../entities";

const user = ref<User>({ name: "", address: "" });

const emit = defineEmits(["submit"]);

function handleSubmite() {
  emit("submit", user.value);
}
</script>

<template>
  <form @submit.prevent="handleSubmite()">
    <div class="mb-3">
      <label for="name" class="form-label">Name : </label>
      <input
        type="text"
        v-model="user.name"
        class="form-control"
        id="name"
        aria-describedby="name"
      />
    </div>
    <div class="mb-3">
      <label for="address" class="form-label">Address : </label>
      <input
        type="text"
        v-model="user.address"
        class="form-control"
        id="address"
      />
    </div>
    <button type="submit" class="btn btn-primary">Add</button>
  </form>
</template>

<style scoped></style>
