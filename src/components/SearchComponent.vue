<template>
    <div class="container d-flex mb-3 justify-content-center">
        <form class="row row-cols-lg-auto g-3 align-items-center" @submit.prevent="filterChar">
            <div class="col-12">
                <label class="visually-hidden" for="inlineFormInputGroupUsername">Username</label>
                <div class="input-group">

                    <input type="text" class="form-control" id="inlineFormInputGroupUsername" placeholder="Username">
                </div>
            </div>

            <div class="col-12">

                <select class="form-select" v-model="search">
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
export default {
    name: 'SearchComponent',
    data() {
        return {
            categoryOptions: [
                'Breaking Bad',
                'Better Call Saul'
            ],
            search: ''
        }
    },

    methods: {
        filterChar() {
            console.log(this.search)
            this.$emit('foundChar', this.search)
        },

        resetSearch() {
            this.search = '';
            this.$emit('foundChar', this.search)

        }
    }
}
</script>

<style lang="scss" scoped>

</style>