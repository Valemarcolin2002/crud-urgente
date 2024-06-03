<template>

  <section class="container-fluid">
    <div class="row min-vh-100">
      <h1 class="col-12 text-center my5">CRUD</h1>
      
      <div class="col-12 col-md-6">

        <!-- FORM -->
        <!-- <Form :users="users"/> -->

        <!-- COMPONENTE FORM -->
        <form v-on:submit="(event)=>preventEvent(event)">

          <!-- name -->
          <div class="mb-5 d-flex justify-content-between">
              <label for="name" class="me-2">name</label>
              <input type="text" id="name" class="input-custom" placeholder="scrivi qui il tuo nome" v-model="tempName">
          </div>

          <!-- surname -->
          <div class="mb-5 d-flex justify-content-between">
              <label for="surname" class="me-2">surname</label>
              <input type="text" id="surname" class="input-custom" placeholder="scrivi qui il tuo cognome" v-model="tempSurname">
          </div>

          <!-- email -->
          <div class="mb-5 d-flex justify-content-between">
              <label for="email" class="me-2">email</label>
              <input type="email" id="email" class="input-custom" placeholder="scrivi qui la tua e-mail" v-model="tempEmail">
          </div>

          <!-- number -->
          <div class="mb-5 d-flex justify-content-between">
              <label for="number" class="me-2">phone number</label>
              <input type="tel" id="number" class="input-custom" placeholder="scrivi qui il tuo numero di telefono" v-model="tempNumber">
          </div>

          <!-- skills -->
          <div class="mb-5 d-flex justify-content-between">
              <label for="skills">skills</label>
              <textarea class="textarea-custom" name="mySkills" id="skills" cols="80" rows="10" placeholder="scrivi qui le tue abilità e le tue capacità" v-model="tempSkills"></textarea>
          </div>

          <!-- BOOTTONE per inviare i dati -->
          <div class="d-flex justify-content-end mb-3">
              <button @click="addUser" class="btn btn-custom" type="submit">aggiungi</button>
          </div>

        </form>
        <!-- FINE COMPONENTE FORM -->

      </div>

      <div class="col-12 col-md-6 d-flex justify-content-evenly flex-wrap">

        <!-- CARDS -->
        <Cards  :users="users" @dettaglio="(utente)=>showDetail(utente)"/>
        
      </div>

    </div>
  </section>

  <!-- componente dell'offcanvas -->
  <UserDetail :user="user"/>

</template>

<script>
// import Form from './components/form.vue'
import Cards from './components/Cards.vue'
import UserDetail from './components/UserDetail.vue'

export default {
  name: 'App',
  
  // components: {Form , Cards},
  components: {Cards, UserDetail},

  data(){
    return{

      //OGGETTO contente i dati delle cards
      users: [
        {id: 1, name: 'Ron', surname: 'Weasley', email: 'Ronilmagnificomagodihogwarts@gmail.com', number: 3373363352, skills:'mi piace mangiare'},
        {id: 2, name: 'Harry', surname: 'Potter', email: 'HarryPotterilprescelto@gmail.com', number: 3383373361, skills: 'sono il prescelto, so parlare in serpentese, ho sconfitto Voldemort, so volare molto bene con la scopa'},
        {id: 3, name: 'Hermione', surname: 'Granger', email: 'HermioneGranger79@gmail.com', number: 3393383370, skills: 'Ho sempre avuto il massimo in ogni corso da me frequentato, sono uscita da Hogwarts con il 100 e lode, utilizzo perfetto delle arti magiche e conoscenza superiore in pozioni, botanica magica e lingue antiche, ho aiutato nella sconfitta di colui che non si può nominare'},
        {id: 4, name: 'carta', surname: 'd\'avanzo', email: 'cartadavanzo@gmail.com', number: 3373363351, skills:'sono solo una carta in più'},
      ],

    //componente form
      //proprietà per salvare in tempo reale il contenuto degli input con il v-model
      tempName: "",
      tempSurname: "",
      tempEmail: "",
      tempNumber: "",
      tempSkills: "",
      //per fare in modo che l'id delle cards siano dinamici
      tempId: 1,

      //oggetto vuoto per salvare i dati prima di inserirli all'interno di users
      user:{},
    //fine componente form

    } 
  },

  //componente form
  methods:{

    //funzione per creare le cards
    addUser(){
      if(this.tempName != '' && this.tempSurname != '' && this.tempEmail != '' && this.tempNumber != '' && this.tempSkills){

        this.tempId = this.users.length + 1

        this.user = {id: this.tempId, name:this.tempName, surname:this.tempSurname, email:this.tempEmail, number:this.tempNumber, skills:this.tempSkills}

        this.users.push(this.user)
        //per svuotare i campi degli input una volta creatasi la cards
        this.tempName = "";
        this.tempSurname = "";
        this.tempEmail = "";
        this.tempNumber = "";
        this.tempSkills = "";
      }
    },

    //funzione per evitare l'aggiornamento della pagina quando si usa il pulsante aggiungi
    preventEvent(e){
      e.preventDefault();
    },

    //funzione per salvare i dati del singolo utente, arrivati da cards.vue, in user
    showDetail(utente){
      this.user = utente
    }

  }
  //fine componente form

}
</script>

<style>

/* tutta roba del form */

/* INPUT */

.input-custom{
        background-color: transparent;
        border:none;
        border-bottom: 2px solid rgb(123,246,218);
        color:rgb(123,246,218);
        width:80%;
    }

    .input-custom::placeholder{
        color:rgb(123,246,218);
        opacity: 0.3;
    }
  
    /* togliere il quadrato che appare quando si digita */
    .input-custom:focus-visible{
        outline:none;
    }

/* fine input */

/* TEXT-AREA */

    .textarea-custom{
        background-color: transparent;
        border: 2px solid rgb(123,246,218);
        color:rgb(123,246,218);
        width:80%;
    }

    .textarea-custom::placeholder{
        color:rgb(123,246,218);
        opacity: 0.3;
    }
  
    /* togliere il focus che appare quando si digita */
    .textarea-custom:focus-visible{
        outline:none;
    }
    
/* fine text-area */

/* BOTTONE */

    .btn-custom{
        padding: 20px 30px;
        background-color: transparent;
        border: 2px solid;
        border-radius: 20px;
        color: rgb(123,246,218);
        transition: 0.4s;
    }

    .btn-custom:hover{
        background-color: rgb(123,246,218);
        color: rgb(3,0,46);
    }

/* fine bottone */


</style>
