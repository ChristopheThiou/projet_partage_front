<template>
  <header>
    <nav class="navbar navbar-expand-lg bg-body-secondary">
      <div class="container-fluid">
        <NuxtLink class="navbar-brand" to="/"
          ><img width="5%" src="/assets/images/echange.png" alt="icon"
        /></NuxtLink>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <NuxtLink
                class="nav-link active"
                aria-current="page"
                to="http://localhost:3000/"
                >Home</NuxtLink
              >
            </li>
            <li class="nav-item">
              <NuxtLink
                class="nav-link"
                to="http://localhost:3000/annonces-list"
                >Annonces</NuxtLink
              >
            </li>
            <li class="nav-item">
              <NuxtLink class="nav-link" to="http://localhost:3000/add-annonces"
                >Ajoutez une annonce</NuxtLink
              >
            </li>
            <li class="nav-item">
              <NuxtLink class="nav-link" to="http://localhost:3000/emprunt-list"
                >Liste emprunt</NuxtLink
              >
            </li>
          </ul>
          <form class="d-flex" role="search" @submit.prevent="search()">
            <input
              v-model="term"
              class="form-control me-2"
              type="search"
              placeholder="Search"
              aria-label="Search"
            />
            <button class="btn btn-outline-success" type="submit">
              Search
            </button>
          </form>
        </div>
      </div>
    </nav>
  </header>
  <div class="container-fluid">
    <div>
      <NuxtPage />
    </div>
  </div>
</template>

<script setup lang="ts">
const term = ref("");

const router = useRouter();

function search() {
  router.push({ path: "/annonces-list", query: { search: term.value } });
}
</script>
