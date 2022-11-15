<template>
    <div>
        <div v-html="`Found ${store.characterList.length} characters`"
            class="match fw-bold rounded-5 col-3 text-center m-auto">
        </div>
    </div>
</template>

<script>
import { store } from '../store';
export default {


    name: 'counterComponent',

    data() {
        return {
            store,
        }
    }
}


</script>

<style lang="scss">

</style>