<template>

    <div v-for="user in users" class="card-custom text-center mt-3 mb-3">
        <p class="h3 mb-3 mt-3">{{ user.id }} | {{ user.name }} {{ user.surname }}</p>
        <button @click="sendDetail(user)" class="btn btn-custom mb-3" data-bs-toggle="offcanvas" data-bs-target="#offcanvasWithBothOptions" aria-controls="offcanvasWithBothOptions">  VEDI DETTAGLI </button>
        <div class="d-flex justify-content-between mb-3">
            <button class="btn btn-outline-change">MODIFICA</button>
            <button class="btn btn-outline-delete">ELIMINA</button>
        </div>
    </div>

</template>

<script>

export default{
    name: 'Cards',

    //proprietà passate
    props: ['users'],

    methods:{
        sendDetail(utente){
            this.$emit('dettaglio', utente)
        }
    }
}

</script>

<style>

/* customizzazione generale della card */
.card-custom{
    height: max-content;
    width: 35%;
    border: 2px solid rgb(123,246,218);
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
}
.a-capo{
    word-break:break-all;
}

/* pulsante modifica */
.btn-outline-change{
    background-color: transparent;
    border: 1px solid beige;
    color: beige; 
    transition: 0.4s;
}
.btn-outline-change:hover{
    background-color: beige;
    color: rgb(3, 0, 46);
}

/* pulsante elimina */
.btn-outline-delete{
    background-color: transparent;
    border: 1px solid coral;
    color: coral; 
    transition: 0.4s;
}
.btn-outline-delete:hover{
    background-color: coral;
    color: rgb(3, 0, 46);
}

</style>

