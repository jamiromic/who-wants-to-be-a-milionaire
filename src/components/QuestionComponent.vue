<template>
    <div>
        <div class="container">
            <div class="triangle left"></div>
            <span>{{ questions[casualNumber].question }}</span>
            <div class="triangle right"></div>
        </div>

    </div>
</template>

<script>
import questions from '@/questions';
import casualNumber from '@/casual';

    export default {
        name: 'QuestionComponent',

        data() {
            return {
                questions : questions,
                casualNumber : casualNumber
            };
        
        },
        
    }

</script>

<style lang="scss" scoped>

.container {
    padding-top: 2.5rem;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;

    span {
        color: #F9FAFB;
        border-top: 2px solid #F9FAFB ;
        border-bottom: 2px solid #F9FAFB ;
        min-width: fit-content;
        width: 40%;
        padding: 1.5rem 0;
        
    
    }

    .triangle {
        width:  4.25rem;
        height: 4.25rem;

        &.left  { 
        transform: rotate(30deg) skewX(-30deg) scale(1,.866); 
        border-left: 2px solid white; 
        border-bottom: 2px solid white;
        border-radius: 0 0 0 50%;
        margin-right: -2.25rem;
        
        }
        &.right { 
        transform: rotate(30deg) skewX(-30deg) scale(1,.866); 
        border-right: 2px solid white; 
        border-top: 2px solid white;
        margin-left: -2.20rem;
        border-radius: 0 50% 0 0;
        
        }



    }

  
    


}



</style>