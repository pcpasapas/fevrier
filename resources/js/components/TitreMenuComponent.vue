<template>
    <div class="menu">
        <ul class="menuUl">
            <router-link :to="{ name:'Home'}">
                <li class="menuli" @click="fetchAllData()">Acceuil</li>
            </router-link>
            <li class="menuli" @click="effacepanier()">Dépannage / Recupération de données</li>
            <router-link :to="{ name:'Montage'}">
                <li class="menuli" @click="effacepanier()">Montage PC complet</li>
            </router-link>
            <router-link :to="{ name:'ComposantsView'}">
                <li class="menuli" @click="effacepanier()">Achat de pieces détachées</li>
            </router-link>
            <router-link :to="{ name:'DevisView'}">
                <li class="menuli" @click="effacepanier()">Demande de devis</li>
            </router-link>
            <li class="menuli" @click="effacepanier()">Création de sites internet</li>
        </ul>
    </div>   
</template>

<script>
// import router from '../router'
import axios from 'axios';
import store from '../store';

export default {
	name: "TitreMenu",
    // components: router,
    data: function () {
        return {
            allData:[]
        }
        // eslint-disable-next-line no-unused-labels 
    },
    methods: {
        fetchAllData(){
            console.log("entree dans la fonction")
            // axios.get('http://127.0.0.1:8000/api/alims')
            //     .then(res => {
            //         console.log(res.data)
            //         this.allData = res.data
            //         console.log(this.allData)
            //     })
            axios.get('http://127.0.0.1:8000/api/alimentations')
                .then(res => {
                    console.log(res.data)
                })
            
                
            },
    
        effacepanier(){
            console.log("effacepanier")
            this.$store.commit("EFFACER_PANIER")
        }
    }
}
</script>



<style>
@import url('https://fonts.googleapis.com/css2?family=Dosis&family=Licorice&family=Shizuru&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');
:root {
    --bleu: rgb(62, 176, 180);
    --bleufonce: rgb(71, 8, 243);
}

body {
    font-family: 'Dosis', sans-serif;
}

.div {
    display: flex;
}
p {
    user-select: none;
}

li {
    user-select: none;
}

.menuUl {
    list-style-type: none;
    border-radius: 20px;
    background-color:rgba(184, 201, 248, 0.842);
    justify-content: space-around;
    display: flex;
    margin-top: 20px
}

.menuli {
    border: 1px solid black;
    text-align: center;
    border-radius: 20px;
    list-style-type: none;
    background-color: white;
    display: grid;
    margin: 10px;
    padding: 10px;
    flex-wrap: wrap;
    align-content: center;
    justify-content: center;
    transition: transform 0.5s;
    cursor:pointer;
}

.menuli:hover {
    background-color: var(--bleufonce);
    transform: scale(1.1);
    color: white;
}
</style>

