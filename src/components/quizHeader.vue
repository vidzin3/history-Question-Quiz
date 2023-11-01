<template>
    <v-progress-linear 
        :model-value="progress"
        color="light-blue"
        striped
        height="40" 
        class="text-h5"
        >
        {{ progress }} %
    </v-progress-linear>
    <v-card class="mt-4" :elevation="4">
        <v-card-title>{{ quiz.name }}</v-card-title>
        <v-card-title class="py-4 d-flex align-center">Question Count <span class="bg-black pa-2 rounded mx-4">{{ questionCount }}</span>
            <v-spacer></v-spacer>
            <v-btn color="red" @click="reloadPage">Again</v-btn>
        </v-card-title>
    </v-card>
</template>

<script>
    export default {
        props:['progress','questionCount','quiz'],
        methods:{
            reloadPage(){
                window.location.reload()
            }
        }
    }
</script>