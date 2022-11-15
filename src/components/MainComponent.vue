<template>
    <SearchComponent @foundChar="getCharacters" />
    <section class="container card-container">
        <counterComponent />
        <div class="container d-flex justify-content-center mt-4 mb-2">

        </div>
        <CardComponent :characters="store.characterList" :loading="store.loading" />

    </section>

</template>

<script>
import axios from 'axios';
import counterComponent from './counterComponent.vue';
import CardComponent from './CardComponent.vue';
import SearchComponent from './SearchComponent.vue';
import { store } from '../store'
export default {
    name: 'MainComponent',
    components: {
        CardComponent,
        SearchComponent,
        counterComponent
    },
    data() {
        return {
            store,
            endPoint: '/characters'

        }
    },
    methods: {
        getCharacters(category) {

            let options = null
            if (category) {
                options = {
                    params: {
                        category: category,

                    }
                }

            }
            store.loading = true;
            const url = store.apiUrl + this.endPoint
            axios.get(url, options).then(
                (res) => {
                    store.characterList = [...res.data];
                    console.log(store.characterList)
                    store.loading = false
                }
            ).catch((error) => {
                store.loading = false

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