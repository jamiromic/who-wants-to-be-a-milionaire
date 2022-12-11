<template>
  <div id="app">
    <header>
      <img width="370" alt="Logo Who Want To Be A Milionaire" src="./assets/Logo.png">
    </header>
    <ContainerComponent/>
  </div>
</template>

<script>
import ContainerComponent from './components/ContainerComponent.vue';


export default {
  name: 'App',
  components: {
    ContainerComponent
  }
}
</script>

<style lang="scss">

#app {
  text-align: center;

  header {
  background-color: #0B0B8B;
  padding: 3rem 0 3rem 0;

  }
  
}



</style>
