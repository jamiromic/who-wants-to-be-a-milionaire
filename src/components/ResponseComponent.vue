<template>
    <div>
        <div class="wrapper">
            <div @click="clickOn()" v-for="(response,i) in questions[randomNumber].responses" :key="i"
            class="response">
                <div class="triangle left"></div>
                <span :id="i">{{ response.text }}</span>
                <div class="triangle right"></div>
            </div>
        </div>
    </div>
</template>

<script>
import questions from '@/questions';

    export default {
        name: 'ResponseComponent',
        props: ['randomNumber'],
        
        data() {
            return {
                questions : questions,
            };
        
        },
        methods: {
            clickOn() {
                const elClicked = event.target;
                const elClickedId = event.target.id;
                const responseUserObj = questions[this.randomNumber].responses[elClickedId];
                
                const responseUser = responseUserObj.result;

                if (responseUser) {
                    elClicked.classList.add('isTrue');
                    
                } else {
                    elClicked.classList.add('isFalse');
                }

                setTimeout(() => {
                    // Rimuovi la classe 'isTrue' o 'isFalse' dall'elemento
                    elClicked.classList.remove('isTrue');
                    elClicked.classList.remove('isFalse');
                    // Modifico il valore della prop dal componente figlio
                    this.$emit('update:randomNumber', this.casualNumber());
                }, 2000); // Cambia il numero dopo 5 secondi

                return responseUser;
            },
            casualNumber() {
                return Math.round(Math.random() * 3);
            },
        },
       
    }

</script>

<style lang="scss" scoped>

.wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    max-width: 1400px;
    margin: 0 auto;
    padding: 5rem;
    gap: 2rem 5rem;

    

    .response {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 500px;
        cursor: pointer;


        span {
            color: #F9FAFB;
            border-top: 2px solid #F9FAFB ;
            border-bottom: 2px solid #F9FAFB ;
            padding: 1.25rem 0;
            width: 100%;
        
        }

        .isTrue {
            background-color: green;
        }

        .isFalse {
            background-color: red;
        }

        .triangle {
        width:  4rem;
        height: 4rem;

            &.left  { 
            transform: rotate(30deg) skewX(-30deg) scale(1,.866); 
            border-left: 2px solid white; 
            border-bottom: 2px solid white;
            border-radius: 0 0 0 50%;
            margin-right: -1.90rem;
            
            }
            &.right { 
            transform: rotate(30deg) skewX(-30deg) scale(1,.866); 
            border-right: 2px solid white; 
            border-top: 2px solid white;
            margin-left: -2rem;
            border-radius: 0 50% 0 0;
            
            }

        }

    }
}

</style>