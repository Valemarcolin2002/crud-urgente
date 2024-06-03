<template>

    <div class="offcanvas offcanvas-start" data-bs-scroll="true" tabindex="-1" id="offcanvasWithBothOptions" aria-labelledby="offcanvasWithBothOptionsLabel">
        <div class="offcanvas-header mb-5">
            <h2 class="offcanvas-title" id="offcanvasWithBothOptionsLabel">{{ user.name }} {{ user.surname }}</h2>
            <button type="button" class="btn-close color-azzurro" data-bs-dismiss="offcanvas" aria-label="Close"></button>
        </div>
        <div class="offcanvas-body">
            <div  class="mb-5">              
                <p class="lead">email:</p>           
                <p class="fst-italic">{{user.email}}</p>                
            </div>
            <div class="mb-5"> 
                <p class="lead">numero:</p>
                <p class="fst-italic">{{ user.number }}</p>
            </div>
            <div class="mb-5"> 
                <p class="lead">skills:</p>
                <p class="fst-italic">{{ user.skills }}</p>
            </div>
            
        </div>
    </div>
 
</template>

<script>
export default{
    props: ['user']
}
</script>

<style>
.offcanvas{
    background-color: transparent;
    backdrop-filter: blur(3px);
    color: rgb(123,246,218);
}
.color-azzurro{
    background-color: rgb(123,246,218);
}
</style>





