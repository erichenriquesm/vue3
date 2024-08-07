<script setup lang="ts">
import Cabecalho from '@/components/Cabecalho.vue';
import Usuario from '@/components/Usuario.vue';
import { ref } from 'vue';
const showComponent = ref(true);
</script>

<template>
  <main>
    <button @click="showComponent = !showComponent">Toggle</button>
    <NavBar/>
    <Cabecalho/>
    <Usuario v-if="showComponent"/>
  </main>
</template>

<style>
*{
  margin: 0;
  padding: 0;
}
</style>
