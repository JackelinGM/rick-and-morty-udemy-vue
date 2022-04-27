<template>
  <div class="titulo d-flex justify-content-center">
    <div class="btn-container">
      <button class="btn-prev" v-on:click="prevPagina">
        PREV
      </button>
      <button class="btn-next" v-on:click="nextPagina">
        NEXT
      </button>
    </div>
  </div>
</template>

<script>

import { useStore } from 'vuex'

export default {
  name: "Pagination",
  data() {
    const store = useStore();
    console.log(store,'storeaki')

    const setCharacters = ((results) => {
      store.dispatch('setCharactersPagination', results);
    })

    return {
      page:1,
      setCharacters
    }
  },
    


  methods: {

    async nextPagina(pag) {
      this.page;
      if (pag) {
        if (this.page <= 41) {
          this.page++;
          const url = `https://rickandmortyapi.com/api/character?page=${this.page}`;
          console.log(this.page);
          console.log(url);
          try {
            const data = await fetch(url);
            const getCharacters = await data.json();
            this.characters = getCharacters;

            this.setCharacters(this.characters);
          } catch (error) {
            console.log(error);
            throw error;
          }
        } else {
          this.page = 42;
        }
      }
    },
    async prevPagina(pag) {
      this.page;
      if (this.page >= 2) {
        this.page--;
        const url = `https://rickandmortyapi.com/api/character?page=${this.page}`;
        console.log(this.page);
        console.log(url);
        try {
          const data = await fetch(url);
          const getCharacters = await data.json();
          this.characters = getCharacters;
          this.setCharacters(this.characters);
          console.log(this.characters);
        } catch (error) {
          console.log(error);
          throw error;
        }
      } else {
        this.page = 1;
      }
    },
  }
  
};
  
</script>

<style>
.btn-container {
  display: flex;
  justify-content:right;
}
.btn-prev, .btn-next {
  border-radius: 4px;
  width: 100px;
  height: 40px;
  font-family:monospace;
  color: black;
  font-size: 15px;
  background: aquamarine;
  border-color: azure;
  margin-left: 20px;
}

</style>
