<script>
import SingleCard from './SingleCard.vue';
import store from '../data/store.js';
import axios from 'axios';

export default {

    name: "AppMain",
    components: {
        SingleCard,
    },

    data() {
        return {
            store,
            searchType: ""
        }
    },

    methods: {
        getArchetype() {
            console.log(this.searchType)
            axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=10&archetype=${this.searchType}`).then(risultato => {
                this.store.cards = risultato.data.data
                this.searchType = ""
            })
        }
    },

    mounted() {

    }
}
</script>

<template>
    <main class="container px-5 py-2">
        <!-- SEZIONE SELECT -->
        <section id="input" class="container mb-2 text-center text-sm-start">
            <!-- AL V-MODEL DEL SELECT DO IL VALORE DI SEARCHTYPE -->
            <select name="type" id="" class="w-25 px-0" @change="getArchetype()" v-model="searchType">
                <!-- AL VALUE DELLE OPTION DO IL VALORE DELLA LISTA ARCHETYPENAME E COSI FACENDO OGNI VOLTA CHE CAMBIO IL VALORE MI CAMBIA IL SEARCH INPUT -->
                <option :value="archetype.archetype_name" v-for="archetype in store.archetypeList">
                    {{ archetype.archetype_name }}
                </option>
            </select>

        </section>
        <!-- SEZIONE CARD -->
        <section id="card" class="container bg-white p-4">
            <div class="content-card text-white">
                <div class="found p-2 bg-dark mx-md-1">
                    <h6 class="m-0 px-0 px-sm-3">Hai trovato: {{ store.cards.length }} cards</h6>
                </div>
                <div class="row m-0 justify-content-between">
                    <SingleCard v-for="cardSingle in store.cards" :card="cardSingle" />
                </div>
            </div>
        </section>
    </main>
</template>

<style scoped>
main {
    background-color: #D48F38;
}
</style>