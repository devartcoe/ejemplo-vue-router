<script setup>

//para traer los parametros de la tuta y podamos usarlo dinamicamente
import { useRoute, useRouter } from "vue-router";
//importamos el composable
import { useGetData } from "@/composables/getData";

// usamos los datos que nos trae el composable
const { data, getData, loading,errorData } = useGetData();

const route = useRoute();
const router = useRouter();
//const poke = ref({});

const back = () => {
  router.push("/pokemons");
};


getData( `https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
</script>
<!-- se le puso el ? por un error ya que trataba de pintar la img antes de obtener los datos
    a esto se le llama optional chaining
-->
<template>
    <p v-if="loading">cargando Informacion...</p>
    <div class="alert alert-danger mt-3" v-if="errorData"><span class="fs-4 ">No existe el pokemon</span></div>
  <div v-if="data">
    <img :src="data.sprites?.front_default" alt="" width="200" />
    <h1>Poke name: {{ $route.params.name }}</h1>
  </div>
  
<div class="mt-5">
    <button @click="back" class="btn btn-outline-primary">Regresar</button>
</div>
  
</template>
