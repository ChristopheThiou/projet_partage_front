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
    <p>
    <label for="name">Name : </label>
    <input type="text" v-model="user.name" placeholder="Type a name ..." />
  </p>
  <p>
    <label for="address">Address : </label>
    <input type="text" v-model="user.address" placeholder="Type a address ..." />
  </p>
    <button class="btn btn-primary">Add</button>
  </form>
</template>

<style scoped></style>