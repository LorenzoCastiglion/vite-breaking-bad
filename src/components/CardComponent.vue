<template>
    <div class="container">
        <div v-if="loading">
            Sto caricando i dati
        </div>


        <div class="row" v-if="!loading">
            <div class="col-2 m-3" v-for="(item, index) in characters" :key="item.char_id">
                <div class="character text-center">
                    <div class="img-container">
                        <img :src="item.img" :alt="item.name">
                    </div>
                    <p class="fw-bold mt-3 text-white title">{{ item.name }}</p>
                    <p class="category mt-3">{{ item.category }}</p>
                    <p class="status">{{ item.status }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'CardComponent',
    props: ['characters', 'loading']
}

</script>

<style lang="scss">
@use '../assets/styles/partials/variables' as *;

.character {
    padding: 15px;
    background-color: $bg-color;
    height: 100%;

    p {
        margin: 0;
        color: $text-gray;
    }

    .title {
        font-size: 17px;
    }

    .status {
        font-size: 14px;
    }

    .img-container {
        height: 150px;
        overflow: hidden;
    }
}
</style>