<script>

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
  }, 
  data(){
    return {
      cards: [],
      archetypes: []
    }
  },
  created(){
    
    axios
    .get("https://db.ygoprodeck.com/api/v7/cardinfo.php")
    .then((response) =>{
      this.cards = response.data.data.slice(0,20);
      console.log(this.cards);
    });

    axios
    .get("https://db.ygoprodeck.com/api/v7/archetypes.php")
    .then((response) =>{
      console.log(response.data);
      for(let i=0; i<response.data.length; i++){
        console.log(response.data[i].archetype_name);
        this.archetypes.push(response.data[i].archetype_name);
      }
      console.log(this.archetypes);
    });

  }
}

</script>

<template>

  <AppHeader/>

  <AppMain :cardsList="cards" :cardsCounter="cards.length" :cardsArchetypes="archetypes"/>
  
</template>

<style lang="scss">
@use "./styles/main.scss"
</style>
