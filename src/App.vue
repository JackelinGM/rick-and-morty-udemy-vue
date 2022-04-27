<template>
  <div class="container">
    <h1>Rick and Morty</h1>
    <FilterByStatus />
    <FilterByName />
    <Pagination />
    <ListCharacters />
    <Pagination />
    <Footer />
    </div>
</template>

<script>

import ListCharacters from '@/components/ListCharacters.vue'
import FilterByStatus from './components/FilterByStatus.vue'
import Pagination from './components/Pagination.vue'
import FilterByName from './components/FilterByName.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    ListCharacters, 
    FilterByName,
    FilterByStatus,
    Pagination,
    Footer
  
  }
}
</script>

<style lang="scss">
:root {
  --background-body:#24282f;
  --background-card:#3c3e44;
  --text-white:#ffffff;
  --text-gray:#c0c0c0;
  --text-orange:#ff9800;
}
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
background: url('./assets/Captura.JPG');
color: var(--text-white);
font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
h1 {
  margin-bottom: 3rem;
  text-align: center;
  color: aqua;
}
.container {
  width: 980px;
  max-width: 90%;
  margin: 5rem auto;
}
img {
  width: 100%;
}
</style>
