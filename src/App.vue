<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <!-- exemple de div faisant appel à un component -->
    <!--
    <div>
      <HelloWorld msg="You did it!" />
    </div> 
    -->
  </header>

  <main>

    <h1>Titre de mon application Vue.js</h1>

    <!-- Composant simple ave cun message personnalisé-->
    <HelloWorld msg="Bonjour Tout le monde" />

    <!--Composant avec des variables objets dynamiques - modifiables avec des inuputs - -->
    <Bienvenue :bienvenue="msg2" :nom="nom" :age="age" :subTitle="subTitle"  />
    <!--ajout d'une phrase créée à partir des autres valeurs-->
    <span>{{ sentence }}</span>
    <div>
      Mon identité: <span>{{ identity }}</span>
    </div>
    <!--ajout de condition avec vue-->
    <div v-if=" age < 40 ">
      Son âge est inférieur à 40 <br><br>
    </div>
    <div v-else>
      Je ne dis pas son âge
    </div>
    <!-- Je peux modifier la class de façon dynamique en lui ajoutant une condition-->
    <div :class="{'text-red' : age > 40}"> {{ age }}</div>
    <!-- Ou avec un ternaire-->
    <div class="bold" :class="[ age > 40 ? 'text-red' : 'text-green']"> {{ nom }}</div>
    <!-- je peux ajouter des événements ex: @change signifie qu'à chaque fois que je modifie l'input il s'affiche-->
    <input type="text" v-model="subTitle" @change="display">
    <input type="text" v-model="nom" >
    <input type="text" v-model="age" >

    <!--Composant avec des balises ouvertes pour définir le contenu allant dans le <slot> du composant avec une variable objet-->
    <Users>
      <template v-slot:name>
        <div :class="{'text-green': true }">Mon nom de famille : {{ users.nom }}</div>
      </template>  
      <template v-slot:surname>
        <div class="text-red">Mon prénom : {{ users.prenom }} </div>
      </template>
    </Users>

    <!--Composant communication parent / enfant component-->
    <EventsParentEnfant @update-name="name => display(name)" />

  </main>
</template>


<script setup>
//Notre JS

//exemple d'importation de components
import HelloWorld from './components/HelloWorld.vue'
import Bienvenue from './components/Bienvenue.vue'
import Users from './components/Users.vue'
import EventsParentEnfant from './components/EventsParentEnfant.vue'
// importation de ref ou de reactive de vue pour avoir des variables dynamiques et de computed
import { watch, computed, ref } from 'vue'

//definition de mes variables

// variables du component Bienvenue
const msg2 = ref('mon message de bienvenue')
// definition d'une variable réactive (la modifier dans un input modifiera la valeur de cette variable partout où elle appraît)
// grâce à ref ou reactive
const subTitle = ref('sous-titre.')
// definition d'une variable sous forme d'objet
const nom = ref('John')
watch(nom, (newValue, oldValue) => {
  console.log(newValue, oldValue);
})
const age = ref(30) 
// variable composée, avec des back tip ATTENTION (AltGr 7), ne marche pas avec des variables issues d'objets comme user.name.value
const sentence = computed( () => {
  return `Bonjour, ${msg2.value} et mon sous titre: ${subTitle.value}`;
})
const identity = computed( () => {
  return `${nom.value} ${age.value}`;
})


//variables du component Users
const users = ref({
  nom: 'Einstein',
  prenom:'Alfred'
})

//variables du composant EventsParentEnfant
const display = (name) => {
  console.log('App.vue : ' + name)
}


</script>


<style scoped>
/* Notre CSS personnalisé pour cette page*/
.text-red {
  color: indianred;
}
.text-green {
  color: green;
}
.bold{
  font-weight: bolder;
}

</style>
