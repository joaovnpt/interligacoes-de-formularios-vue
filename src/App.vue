<script setup>
import { ref, reactive } from 'vue'

const titulo = ref('Interligação de Formulários');
let showResult = ref(false);
const categories = [{
  id: 1, name: 'Jewelry'
},
{
  id: 2, name: 'Electronics'
},
{
  id: 3, name: 'Clothes'
},
{
  id: 4, name: 'Sports'
}
]
//const categories = ['Jewelry', 'Electronics', 'Clothes', 'Sports']
const product = reactive({
  name: '',
  price: '',
  categories: [],
  stock: ''
})
function submitForm() {
  if (product.qtd < 0) {
    alert('Stock must be positive.');
    return;
  }
  showResult.value = !showResult.value
}

</script>

<template>
  <h1 class="titulo">{{ titulo }}</h1>
  <div class="container">
    <div class="form-container">
      <form class="vue-form" @submit.prevent="submitForm()">
        <div class="input-container">
          <label for="name">Name:</label>
          <input type="text" id="name" name="name" v-model="product.name" placeholder="Product name" minlength="3"
            maxlength="20" />
          <label for="price">Price</label>
          <input type="number" name="price" id="price" v-model="product.price" placeholder="Product price" />
          <label for="category">Category</label>
          <input type="category" id="category" name="category" v-model="product.category"
            placeholder="Product category" />
          <label for="stock">Stock</label>
          <input type="stock" name="stock" id="stock" v-model="product.stock" placeholder="Stock" />
          <div class="input-container">
            <fieldset>
              <legend>Categories:</legend>

              <div v-for="category in categories" :key="category.id">
                <input type="checkbox" v-model="product.categories" :value="category.id"> {{ category.name }}
              </div>

            </fieldset>

            <button type="submit" class="submit-btn">Show data</button>
          </div>
        </div>
      </form>
    </div>
    <div class="resultado-container" v-if="showResult == true">
      <h3>Product data:</h3>
      <p>Name: {{ product.name }}</p>
      <p>Price: {{ product.price }}</p>
      <p>Category: {{ product.categories }}</p>
      <p>Stock: {{ product.stock }}</p>
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

.input-container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
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
  margin-top: 20px;
}
</style>
