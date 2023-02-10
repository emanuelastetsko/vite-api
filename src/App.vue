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
    });

    axios
    .get("https://db.ygoprodeck.com/api/v7/archetypes.php")
    .then((response) =>{
      for(let i=0; i<response.data.length; i++){
        this.archetypes.push(response.data[i].archetype_name);
      }
    });

  },
  methods:{
    selectArchetype(event) {
      this.cards = [];
      const selectedValue = event.target.value;

      axios
      .get('https://db.ygoprodeck.com/api/v7/cardinfo.php', { 
        params: {
          archetype: selectedValue,
          }
        }).then((response) => {
          this.cards = response.data.data.slice(0,50);
        });

   }
  }
}


</script>

<template>

  <AppHeader/>

  <AppMain :cardsList="cards" :cardsCounter="cards.length" :cardsArchetypes="archetypes" :selectArchetypeFunction="selectArchetype"/>
  
</template>

<style lang="scss">
@use "./styles/main.scss"
</style>
