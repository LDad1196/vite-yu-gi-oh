<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import store from './data/store.js';
import axios from 'axios';
export default {
  components: {
    AppHeader,
    AppMain,
  },

  data() {
    return {
      //richiamo lo store.js in return per far si che ho lo lista delle cards visibile qui
      store
    }
  },
  created() {
    axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php").then(risultato => {
      console.log(risultato.data)

      this.store.archetypeList = risultato.data
      console.log(this.store.archetypeList)
    })

    axios.get(/*dopo num= decido quante carte creare e dopo offset= decido quante me ne deve saltare di quelle inziali della lista*/
      "https://db.ygoprodeck.com/api/v7/cardinfo.php?num=30&offset=10&archetype=Alien").then(risultato => {

        //dichiaro che in store.js la lista cards è uguale al risultato che mi da la funzione che genera le card
        this.store.cards = risultato.data.data

        /* CON QUESTO LINK CREO CARD SENZA IL CARATTERE ALIEN       https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=15*/
      })
  }
}
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style scoped></style>
