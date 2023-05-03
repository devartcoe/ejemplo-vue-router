<script setup>

import { RouterLink } from "vue-router";
//importamos el composable
import { useGetData } from "@/composables/getData";
// usamos los datos que nos trae el composable
const { data, getData, loading, errorData } = useGetData();

getData("https://pokeapi.co/api/v2/pokemon");
</script>

<template>
  <h1 class="display-2 text-warning">Pokemons</h1>
 
  <p v-if="loading">cargando Informacion...</p>
  <div class="alert alert-danger mt-3" v-if="errorData"><span class="fs-4 ">{{ errorData }}</span></div>
  <div v-if="data">
    <ul class="list-group">
      <li v-for="poke in data.results" class="list-group-item">
        <router-link :to="`/pokemons/${poke.name}`">
          <span class="h5" >{{ poke.name }}</span>
        </router-link>
      </li>
    </ul>
    <div>
    <button :disabled="!data.previous" class="btn btn-success me-2" @click="getData(data.previous)">Previous</button>
    <button :disabled="!data.next" class="btn btn-primary" @click="getData(data.next)">Next</button>
  </div>
  </div>
</template>
