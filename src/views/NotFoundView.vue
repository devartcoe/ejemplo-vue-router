<script setup>
 import { useRoute, useRouter } from 'vue-router';
    const router = useRouter();
     const back=()=>{
        router.push('/pokemons');
     }
</script>
<template>
    <h1>404</h1>
    <button @click="back">Regresar</button>
</template>