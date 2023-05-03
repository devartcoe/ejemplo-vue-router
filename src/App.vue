<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
 
 <nav class="navbar bg-body-tertiary">
  <div class="container">
    <router-link class="navbar-brand" to="/">
      <img src="@/assets/logo.svg" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
      PokeApi
    </router-link>
    <div>
      <RouterLink  active-class="active" class="btn btn-outline-primary me-2" to="/" >Home</RouterLink>
      <RouterLink  active-class="active" class="btn btn-outline-primary" to="/pokemons">Pokemons</RouterLink>
    </div>
  </div>
</nav>
 
<div class="container text-center">
  <RouterView />
</div>
 
  
</template>

