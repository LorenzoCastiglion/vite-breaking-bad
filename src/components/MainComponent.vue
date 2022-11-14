<template>
    <section class="container card-container">
        <CardComponent :characters="characterList" :loading="loading" />
    </section>
</template>

<script>
import axios from 'axios';
import CardComponent from './CardComponent.vue';

export default {
    name: 'MainComponent',
    components: {
        CardComponent
    },
    data() {
        return {
            apiUrl: 'https://www.breakingbadapi.com/api/characters',
            characterList: [],
            loading: false
        }
    },
    methods: {
        getCharacters() {
            this.loading = true;
            axios.get(this.apiUrl).then(
                (res) => {
                    this.characterList = [...res.data];
                    console.log(this.characterList)
                    this.loading = false
                }
            ).catch((error) => {
                console.log(error);
            })
        }
    },
    created() {
        this.getCharacters()
    }
}


</script>

<style lang="scss">
@use '../assets/styles/partials/variables' as *;

.card-container {
    background-color: $bg-white;
    padding: 20px;
}
</style>