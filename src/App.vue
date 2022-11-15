<template>

  <header>
    <HeaderComponent />
  </header>

  <main>

    <MainComponent />
  </main>


</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';

export default {
  components: {
    HeaderComponent,
    MainComponent,

  }
}
</script>

<style lang="scss">

</style>