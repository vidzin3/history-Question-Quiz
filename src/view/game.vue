<template>
    <v-card class="d-lg-flex md-block align-center" :elevation="4">
        <v-img :src="game.img" :width="400"></v-img>
        <div class="pa-4 ">
            <v-card-title>{{ game.name }}</v-card-title>
            <v-card-subtitle class="mb-4">history Question is the fun Quiz game out there! Easy to learn history Fact, so is really addictive! And you learn lots about the world at the same time!</v-card-subtitle>
            <v-btn class="mx-4" to="/playgame" color="yellow">Play Now!</v-btn>
        </div>
    </v-card>
</template>

<script>

    export default {
        props:['game']
    }
</script>