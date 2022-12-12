<template>
    <div class="container">
        <QuestionComponent/>
        <ResponseComponent/>
        
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
}

    }
</script>

<style lang="scss" scoped>

.container {
    background-color: #11093A;
    height: 610px;
}

</style>