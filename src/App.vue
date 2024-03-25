<script setup>
import { ref, reactive } from 'vue'

const titulo = ref('Interligação de Formulários')
const user = reactive({
  name: '',
  email: '',
  age: '',
  password: '',
  confirmPassword: ''
})

let msg = ref('');
let showResult = ref(false);

/* function submitForm() {
  submited = true
  if (
    user.value.length !== 0 &&
    user.age.value.length !== 0 &&
    user.email.value.length !== 0 &&
    user.age.value >= 18 &&
    user.age.value <= 60 &&
    user.password.value === user.confirmPassword.value
  ) {
    msg.value = `Form submitted sucessfully!`;
    clearForm()
  } else alert('There was an error, fill in your informations and try again.');
} */
</script>

<template>
  <h1 class="titulo">{{ titulo }}</h1>
  <div class="container">
    <div class="form-container">
      <div class="msg-container" v-show="msg.length != 0">
        <p>{{ msg }}</p>
      </div>
      <form class="vue-form">
        <!--@submit.prevent faz com que ao submitar, o navegador siga as instruções da função prescrita, e não recarregue a página e mande para o servidor (padrão)-->
        <div class="input-container">
          <label for="name">Name:</label>
          <hr />
          <input type="text" id="name" name="name" v-model="user.name" placeholder="Your name" minlength="3"
            maxlength="20" required />
          <hr />
          <label for="age">Age</label>
          <hr />
          <input type="number" name="age" id="age" v-model="user.age" placeholder="Your age" min="18" max="60"
            required />
          <hr>
          <label for="email">E-mail</label>
          <hr />
          <input type="email" id="email" name="email" v-model="user.email" placeholder="Your best e-mail" required />
          <hr />
          <label for="password">Password</label>
          <hr />
          <input type="password" name="password" id="password" v-model="user.password" placeholder="Your best password"
            minlength="8" />
          <hr />
          <label for="confirmPassword">Confirm password</label>
          <hr />
          <input type="password" name="confirmPassword" id="confirmPassword" v-model="user.confirmPassword"
            placeholder="Confirm your password">
          <div class="input-container">
            <button class="submit-btn" @click="showResult = !showResult">Submit</button>
          </div>
        </div>
      </form>
    </div>
    <div class="resultado-container" v-if="showResult == true">
      <h3>User data:</h3>
      <p>Name: {{ user.name }}</p>
      <p>Age: {{ user.age }}</p>
      <p>E-mail: {{ user.email }}</p>
      <p>Password: {{ user.password }}</p>
      <p>{{ showResult }}</p>
    </div>
  </div>
</template>

<style scoped>
.titulo {
  margin-bottom: 10px;
}

.container {
  display: flex;
  flex-direction: row;
  column-gap: 2rem;
}

.form-container,
.resultado-container {
  padding: 10px;
  min-height: 80vh;
  width: 48vw;
  margin-left: 1vh;
  margin-right: 1vh;
  border-radius: 15px;
}

.resultado-container {
  background-color: rgb(130, 171, 207);
}

.form-container {
  background-color: burlywood;
}

.submit-btn {
  position: relative;
}
</style>
