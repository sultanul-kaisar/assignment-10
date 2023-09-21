<template>
  <div class="container">
    <div class="row">
      <div v-for="product in products" :key="product.id" class="col-lg-3 col-md-6 mb-4">
        <div class="product-card">
          <img :src="product.thumbnail" :alt="product.title" class="product-image">
          <div class="product-card-body">
            <h5 class="product-title">{{ product.title }}</h5>
            <p class="product-description">{{ product.description }}</p>
            <p class="product-category">{{ product.category }}</p>
            <h5 class="product-price">${{ product.price }}</h5>
          </div>
          <div class="product-card-footer">
            <button @click="viewDetails(product.id)" class="details-button">View Details</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const products = ref([])

const fetchProducts = async () => {
  const response = await fetch('https://dummyjson.com/products')
  const data = await response.json()
  products.value = data.products
}

onMounted(fetchProducts)

const viewDetails = (id) => {
  router.push({ name: 'ProductDetails', params: { id } })
}
</script>

<style scoped>
.container {
  margin-top: 20px;
}

.product-card {
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 20px;
  margin: 20px;
  max-width: 300px;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
}

.product-card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

.product-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.product-title {
  font-size: 18px;
  font-weight: bold;
  margin: 10px 0;
}

.product-price {
  color: #007BFF;
  font-size: 16px;
  margin: 10px 0;
}

.product-category {
  font-size: 14px;
  color: #6c757d;
  margin: 10px 0;
}

.product-description {
  font-size: 14px;
  margin: 10px 0;
}

.details-button {
  background-color: #007BFF;
  color: white;
  border: none;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 10px 2px;
  cursor: pointer;
  border-radius: 4px;
  transition-duration: 0.4s;
}

.details-button:hover {
  background-color: white;
  color: black;
  border: 2px solid #007BFF;
}
</style>
