<template>
    <div class="container">
        <QuestionComponent :randomNumber="randomNumber"/>
        <ResponseComponent :randomNumber.sync="randomNumber"/>
    </div>
</template>

<script>
import QuestionComponent from './QuestionComponent.vue';
import ResponseComponent from './ResponseComponent.vue';

    export default {
        name: 'ContainerComponent',

        components: {
            QuestionComponent,
            ResponseComponent

        },
        data() {
            return {
            randomNumber: null,
            questionNumbers: [0,1,2,3], // Array per memorizzare i numeri casuali precedenti
            };
        },
        created() {
            this.randomNumber = this.casualNumber();
        },
        methods: {
            casualNumber() {
                const randomIndex = Math.floor(Math.random() * this.questionNumbers.length);
                return this.questionNumbers[randomIndex];
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