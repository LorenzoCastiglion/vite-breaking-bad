<template>
    <div class="container d-flex mb-3 justify-content-center">
        <form class="row row-cols-lg-auto g-3 align-items-center" @submit.prevent="filterChar">
            <div class="col-12">

                <div class="input-group">

                    <input type="text" class="form-control" id="nameSearch" placeholder="A - Z">
                </div>
            </div>

            <div class="col-12">

                <select class="form-select" v-model="store.search">
                    <option value="" selected>Choose...</option>
                    <option :value="category" v-for="(category, index) in categoryOptions" :key="index">{{ category }}
                    </option>

                </select>
            </div>

            <div class="col-12">
                <button type="submit" class="btn btn-primary">Find</button>
            </div>

            <div class="col-12">
                <button type="reset" class="btn btn-danger" @click="resetSearch">Reset</button>
            </div>
        </form>
    </div>
</template>

<script>
import { store } from '../store'
export default {
    name: 'SearchComponent',
    data() {
        return {
            store,
            categoryOptions: [
                'Breaking Bad',
                'Better Call Saul'
            ],

        }
    },

    methods: {
        filterChar() {
            console.log(store.search)
            this.$emit('foundChar', store.search)
        },

        resetSearch() {
            this.search = '';
            this.$emit('foundChar', store.search)

        }
    }
}
</script>

<style lang="scss" scoped>

</style>