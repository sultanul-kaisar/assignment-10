<template>
  <div>
    <img :src="product.thumbnail" :alt="product.title" class="product-image">
    <h2 class="product-title">{{ product.title }}</h2>
    <p class="product-price">${{ product.price }}</p>
    <p class="product-category">{{ product.category }}</p>
    <p class="product-description">{{ product.description }}</p>
    <p class="product-rating">Rating: {{ product.rating }}</p>
    <p class="product-stock">Stock: {{ product.stock }}</p>
    <p class="product-brand">Brand: {{ product.brand }}</p>
    <p class="product-discount">Discount: {{ product.discountPercentage }}%</p>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const product = ref({})

const fetchProduct = async () => {
  const response = await fetch(`https://dummyjson.com/products/${route.params.id}`)
  const data = await response.json()
  product.value = data
}

onMounted(fetchProduct)
</script>

<style scoped>
.product-image {
  width: auto;
  height: 600px;
  object-fit: cover;
}

.product-title {
  font-size: 24px;
  font-weight: bold;
  margin: 10px 0;
}

.product-price {
  color: #007BFF;
  font-size: 20px;
  margin: 10px 0;
}

.product-category {
  font-size: 18px;
  color: #6c757d;
  margin: 10px 0;
}

.product-description {
  font-size: 16px;
  margin: 10px 0;
}

.product-rating {
  font-size: 16px;
  margin: 10px 0;
}

.product-stock {
  font-size: 16px;
  margin: 10px 0;
}

.product-brand {
  font-size: 16px;
  margin: 10px 0;
}

.product-discount {
  font-size: 16px;
  margin: 10px 0;
}
</style>
