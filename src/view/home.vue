<script>
    import data from '../data/db.json'
    import game from '../view/game.vue'
    export default {
        components:{
            game
        },
        data(){
            return {
                data
            }
        },
    }
</script>

<template>
    <v-container fluid>
        <game v-for="game in data.quiz" :game="game" />
    </v-container>
</template>