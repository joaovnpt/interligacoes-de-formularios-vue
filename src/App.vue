<script setup>
import { ref } from 'vue'

const name = ref(''); //tex; minlength; required;
const email = ref(''); //email; required;
const age = ref(''); //number; required;
const submit = ref('');
let msg = ref('')

function submitForm() {
  if (name.value.length !== 0 && age.value.length !== 0 && email.value.length !== 0 && age.value >= 18 && age.value <= 60) {
    msg.value = `Form submitted sucessfully! Confirm your information Name: ${name.value} Age: ${age.value} E-mail: ${email.value}`;
  }
  else alert('There was an error, fill in your informations and try again.')
}

</script>

<template>
  <div class="container">
    <div class="msg-container" v-show="msg.length != 0">
      <p>{{ msg }}</p>
    </div>
    <form class="vue-form" @submit.prevent="submitForm"> <!--@submit.prevent faz com que ao submitar, o navegador siga as instruções da função prescrita, e não recarregue a página e mande para o servidor (padrão)-->
      <div class="input-container">
        <label for="name">Name:</label>
        <hr>
        <input type="text" id="name" name="name" v-model="name" placeholder="Your name" minlength="3" maxlength="20" required>
        <hr>
        <label for="email">E-mail</label>
        <hr>
        <input type="email" id="email" name="email" v-model="email" placeholder="Your best e-mail" required>
        <hr>
        <label for="age">Age</label>
        <hr>
        <input type="number" name="age" id="age" v-model="age" placeholder="Your age" min="18" max="60" required>
      </div>
      <div class="input-container">
        <input type="submit" id="submit" value="Submit" v-model="submit" @click="submitForm()">
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
