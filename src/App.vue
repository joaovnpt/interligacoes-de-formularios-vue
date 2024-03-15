<script setup>
import { ref } from 'vue'

const texto = ref('')
</script>

<template>
  <div class="container">
    <input type="text" v-bind:value="texto" v-on:input="(event) => (texto = event.target.value)" />
    <!-- *v-bind* e *v-on* pode ser substitúido por ":" e "@" 
    @ e : JUNTOS podem ser substituídos por "v-model"
    O input a cima poderia ser <input type="text" v-model="texto" /> -->
    <p>Texto digitado: {{ texto }}</p>
  </div>
</template>

<style scoped></style>
