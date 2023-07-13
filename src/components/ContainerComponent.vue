<template>
    <div class="container">
        <QuestionComponent v-if="!gameOver" 
        :randomNumber="randomNumber"
        />
        <ResponseComponent v-if="!gameOver" 
        :randomNumber.sync="randomNumber" 
        :questionNumbers="questionNumbers" 
        :gameOver.sync="gameOver" @update:gameOver="gameOver = $event"
        :score.sync="score" @update:score="score = $event"
        />
        <FinalResultComponent v-if="gameOver" 
        :score="score"
        :questionNumbers="questionNumbers"
        />
    </div>
</template>

<script>
import QuestionComponent from './QuestionComponent.vue';
import ResponseComponent from './ResponseComponent.vue';
import FinalResultComponent from './FinalResultComponent.vue';
import questions from '@/questions';

    export default {
        name: 'ContainerComponent',

        components: {
            QuestionComponent,
            ResponseComponent,
            FinalResultComponent,

        },
        data() {
            return {
            questions : questions,
            randomNumber: null,
            questionNumbers: questions.length, // Array che contiene l'index delle domande disponibili
            score: 0,
            gameOver: false,
            };
        },
        created() {
            this.randomNumber = this.casualNumber();
        },
        methods: {
            casualNumber() {
                return Math.round(Math.random() * 3);
            }
        }

    }
    
</script>

<style lang="scss" scoped>

.container {
    background-color: #11093A;
    height: 610px;
}

</style>