<template>
    <section class="container card-container">
        <div class="container d-flex justify-content-center mt-4 mb-2">
            <div v-html="`Found ${characterList.length} characters`" class="match fw-bold rounded-5 col-3 text-center">
            </div>
        </div>
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

.match {
    background-color: $bg-barra;
    color: $text-white;
    width: 80%;
    padding: 20px;
}
</style>