<template>
    <div class="panier" v-if="this.$store.state.boitierchoisistore != '' || this.$store.state.alimchoisistore !='' || this.$store.state.processeurchoisistore !=''">
        <ul class=ulpanier>
            <h3 class="non">Votre PANIER : </h3>
            <li class="lipanier" v-if ="this.$store.state.boitierchoisistore != ''" @click="boitierEnleve()">
                <p>{{ this.$store.state.boitierchoisistore.text }}</p>
                <p class="prix" v-if="this.$store.state.boitierchoisistore.prix != null"> {{ this.$store.state.boitierchoisistore.prix }} €</p>
                <p style="color: white">Cliquez pour supprimer et choisir un autre modèle</p>
            </li>
            <li class="lipanier" v-if ="this.$store.state.alimchoisistore != ''" @click="alimEnleve()">
                <p class="p">{{ this.$store.state.alimchoisistore.text }}</p>
                <p class="prix" v-if="this.$store.state.alimchoisistore.prix != null"> {{ this.$store.state.alimchoisistore.prix }} €</p>
                <p class="enleve" style="color: white">Cliquez pour supprimer et choisir un autre modèle</p>
            </li>
            <li class="lipanier" v-if ="this.$store.state.processeurchoisistore != ''" @click="processeurEnleve()">
                <p class="p">{{ this.$store.state.processeurchoisistore.text }}</p>
                <p class="prix" v-if="this.$store.state.processeurchoisistore.prix != null"> {{ this.$store.state.processeurchoisistore.prix }} €</p>
                <p class="enleve" style="color: white">Cliquez pour supprimer et choisir un autre modèle</p>
            </li>
            <li class="lipanier" v-if ="this.$store.state.cartemerechoisistore != ''" @click="cartemereEnleve()">
                <p class="p">{{ this.$store.state.cartemerechoisistore.text }}</p>
                <p class="prix" v-if="this.$store.state.cartemerechoisistore.prix != null"> {{ this.$store.state.cartemerechoisistore.prix }} €</p>
                <p class="enleve" style="color: white">Cliquez pour supprimer et choisir un autre modèle</p>
            </li>
            <li class="lipanier" v-if ="this.$store.state.ssdchoisistore != ''" @click="ssdEnleve()">
                <p class="p">{{ this.$store.state.ssdchoisistore.text }}</p>
                <p class="prix" v-if="this.$store.state.ssdchoisistore.prix != null"> {{ this.$store.state.ssdchoisistore.prix }} €</p>
                <p class="enleve" style="color: white">Cliquez pour supprimer et choisir un autre modèle</p>
            </li>
            <li class="lipanier" v-if ="this.$store.state.cgchoisistore != ''" @click="cgEnleve()">
                <p class="p">{{ this.$store.state.cgchoisistore.text }}</p>
                <p class="prix" v-if="this.$store.state.cgchoisistore.prix != null"> {{ this.$store.state.cgchoisistore.prix }} €</p>
                <p class="enleve" style="color: white">Cliquez pour supprimer et choisir un autre modèle</p>
            </li>
            
            <h3 class="non">
            Prix Total = {{ this.$store.state.prixtotalstore }} €</h3>

        </ul>
        <ul class="ulconfig">
        <h3>Votre Configuration : </h3>
            <li class="liconfig" v-if="this.$store.state.boitierchoisistore != '' || this.$store.state.alimchoisistore !='' || this.$store.state.processeurchoisistore !=''">               
            <img class="imageconfig" :src= this.$store.state.boitierchoisistore.img>
            <ul>
             <li>
            Nombre de ports USB en facade : 4
            </li>
            <li>Alimentation incluse : {{this.$store.state.boitierchoisistore.alim}}</li>
            <li>Format du boitier : {{this.$store.state.boitierchoisistore.format}}</li>
            <li v-if="this.$store.state.alimchoisistore !=''">Puissance de l'alimentation : {{this.$store.state.alimchoisistore.puissance}} w
            </li>            
            <li class="liconfig">
            <img v-if ="this.$store.state.alimchoisistore != ''" class="imageconfigbouge" :src= this.$store.state.alimchoisistore.img>
            </li>
            <li class="liconfig">
            <img v-if="this.$store.state.processeurchoisistore!= ''" class="imageconfigbouge" :src= this.$store.state.processeurchoisistore.img>
            </li>
            <li class="liconfig">
            <img v-if="this.$store.state.cartemerechoisistore != ''" class="imageconfigbouge" :src= this.$store.state.cartemerechoisistore.img>
            </li>
            <li class="liconfig">
            <img v-if="this.$store.state.ssdchoisistore != ''" class="imageconfigbouge" :src= this.$store.state.ssdchoisistore.img>
            </li>
            <li class="liconfig">
            <img v-if="this.$store.state.cgchoisistore != ''" class="imageconfigbouge" :src= this.$store.state.cgchoisistore.img>
            </li>
            </ul>
           </li>
            
            
        </ul>
        <section class="basPanier">Les prix sont donnés à titre indicatifs et varient régulièrement. Demandez un devis pour confirmer les tarifs.</section>
    </div>
</template>

<script>


export default {
    name:"comppanier",
    components: {
    },
    data() {
        return {
            // boitierChoisi:"",
            // prixTotal: 0,
            // processeurChoisi:"",
            // alimChoisi:"",
            // ssdChoisi:"",

            // cartemereChoisi:"",


        }
    },
    created() {
        console.log(this.$store.state.boitierchoisistore)
    },
    methods: {
        boitierEnleve() { 
        this.$store.state.prixtotalstore = this.$store.state.prixtotalstore-parseFloat(this.$store.state.boitierchoisistore.prix)
        this.$store.state.boitierchoisistore=''
        this.$store.state.alimchoisistore=''
        },
        alimEnleve() { 
        this.$store.state.prixtotalstore = this.$store.state.prixtotalstore-parseFloat(this.$store.state.alimchoisistore.prix)
        this.$store.state.alimchoisistore=''
        },
        processeurEnleve() { 
        this.$store.state.prixtotalstore = this.$store.state.prixtotalstore-parseFloat(this.$store.state.processeurchoisistore.prix)
        this.$store.state.processeurchoisistore=''
        },
        ssdEnleve() { 
        this.$store.state.prixtotalstore = this.$store.state.prixtotalstore-parseFloat(this.$store.state.ssdchoisistore.prix)
        this.$store.state.ssdchoisistore=''
        },
        cartemereEnleve() { 
        this.$store.state.prixtotalstore = this.$store.state.prixtotalstore-parseFloat(this.$store.state.cartemerechoisistore.prix)
        this.$store.state.cartemerechoisistore=''
        },
        cgEnleve() { 
        this.$store.state.prixtotalstore = this.$store.state.prixtotalstore-parseFloat(this.$store.state.cgchoisistore.prix)
        this.$store.state.cgchoisistore=''
        },

    }
}
</script>

<style lang="css" scoped>
.p{
    margin-top:10px;
    height: 50%;
}

.prix{
    margin:10px;
    height: 50%;
}
    .panier {
    display: grid;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 30px;
    grid-template-columns: 40% 60%;
    width:80%;
    border: 1px solid black;
    border-radius: 20px;
    justify-content: center;
    text-align: center;
}
.basPanier{
    grid-column-start:1;
    grid-column-end:4;
    text-align:center;
    font-size: 1.5em;
}
.non{
    user-select: none;
       background-color: white;

}

.ulpanier {
    display: grid;

}

.lipanier {
    width:100%;
    height: 100px;
    border: 1px solid black;
    border-radius: 20px;
    display: grid;
    grid-template-columns: 60% 40%;
    /* grid-template-rows: 60% 40%; */
    font-size: 0.8rem;
}
.enleve{
    grid-row:2
}
.liconfig {
    list-style-type: none;
    display: grid;
    width: 100%;
    grid-template-columns: 60% 40%;
}
.ulpanier :hover {
    background-color: red;
    color: white;
}
.non :hover {
   background-color: white;
    color: black; 
}
.imageconfig{
    display:block;
    width:30%;
    height:auto 
}

.imageconfigbouge {
    width:50%;
    transform: translateY(200px);
    transform: translateX(-200%);
    opacity: 100%;
    /* animation-name: slidein; */
    animation: slidedansboitier 5s;
    height:auto
}



@keyframes slidedansboitier {
  from {
    width: 100%;
    transform: translateY(400px);
  }

  to {

    width: 50%;
  }
}

</style>