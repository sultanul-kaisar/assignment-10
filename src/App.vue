<template>
  <div id="app">
    <nav>
      <router-link to="/">My Shop</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'App',
})
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  margin: 0 auto;
  text-align: center;
}

nav {
  background-color: #f8f9fa;
  padding: 10px 0;
}

nav a {
  margin: 0 15px;
  text-decoration: none;
  color: #007bff;
}
</style>
