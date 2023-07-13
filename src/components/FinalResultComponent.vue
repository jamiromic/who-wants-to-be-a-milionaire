<template>
    <div>
        <div class="container">
            <h1 class="result">Il tuo punteggio è di {{ this.score }} su un totale di {{ this.questionNumbers }} domande</h1>
            <a class="new_match" href="" @click="newMatch()">Nuova Partita</a>
        </div>

    </div>
</template>

<script>

    export default {

        name: 'FinalResultComponent',
        props: ['questionNumbers', 'score','gameOver'],

        data() {

            return {
    
            };
        
        },
        methods: {

            //Metodo utilizzato per impostare props gameOver a false, e quindi dare il via a una nuova partita
            newMatch() {
                this.$emit('update:gameOver', false);
            }
        }
        
    }

</script>

<style lang="scss" scoped>

.container {
    padding-top: 2.5rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;

    .result {
        color: whitesmoke;
    }

    .new_match {
        text-decoration: none;
        color: whitesmoke;
        background-color: green;
        padding: 1rem 2rem;
        border-radius: 5px;
        margin-top: 2rem;
    }

    

    

}

</style>