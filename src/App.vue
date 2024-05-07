<script>
import axios from "axios";
import AppCards from "./components/AppCards.vue";
import AppHeader from "./components/AppHeader.vue";
import AppLoading from "./components/AppLoading.vue"


export default {
  components: {
    AppHeader,
    AppCards,
    AppLoading,

  },

  data() {
    return {
      // Array che conterrà i dati dei personaggi
      cardsArray: [],
      // Variabile per gestire lo stato di caricamento
      isLoading: false,
    
    };
  },

  created() {
    this.isLoading = true;

    axios.get("https://rickandmortyapi.com/api/character").then((resp) => {
      console.log(resp);
      // Una volta ottenuti i dati, li assegniamo a cardsArray
      this.cardsArray = resp.data.results;
      

      //otteniamo i dati quindi nascondiamo caricamento
        this.isLoading = false;
        
      
      
    });
  },
  methods: {
    // Metodo per ottenere i dati dei personaggi in base ai filtri
    getCards() {
      this.isLoading = true;
      // Costuriamo i parametri per la chiamata axios
       const paramsObj = {};

     


      //chiamata GET all'API
      axios
        .get("https://rickandmortyapi.com/api/character", {
          params: paramsObj,
        })

        // Una volta ottenuti i dati, li assegniamo a cardsArray
        .then((resp) => {
          this.cardsArray = resp.data.results;
          this.isLoading = false;
        });
    },
  },
};
</script>

<template>
  <AppHeader />
  <AppLoading v-if="isLoading" />
  <AppCards v-else :cardsArray="cardsArray" />
</template>

<style lang="scss"></style>