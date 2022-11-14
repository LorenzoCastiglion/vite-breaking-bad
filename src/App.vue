<template>

  <header>
    <HeaderComponent />
  </header>

  <main>
    <SearchComponent />
    <MainComponent />
  </main>


</template>

<script>

import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import SearchComponent from './components/SearchComponent.vue';


export default {

  components: {
    HeaderComponent,
    MainComponent,
    SearchComponent
  }
}

</script>

<style lang="scss">

</style>