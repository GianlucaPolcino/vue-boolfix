<template>
    <header class="container-flex">
        <div class="row h-100 w-100 align-items-center justify-content-between">
            <div class="col ps-4">
                <h1 class="text-danger">
                    BoolFlix
                </h1>
            </div>
            <div class="col text-end">
                <button class="btn btn-primary align-middle me-3" @click="sendToApp">Cerca</button>
                <input v-model="search" @keyup.13="sendToApp" type="text">
            </div>
        </div>
        
    </header>
</template>

<script>
export default {
    name: "Header",

    data(){
        return{
            search: 'ritorno al futuro',
        }
    },

    methods:{
        sendToApp(){
            this.$emit('search', this.search);
            this.search = '';
        }
    },

    mounted(){
        this.sendToApp()
    },
}
</script>

<style lang="scss">
    header{
        height: 100px;
        background-color: black;
    }
</style>