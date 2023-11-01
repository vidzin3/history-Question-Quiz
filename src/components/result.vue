<template>
    <v-card>
        <v-card-title class="text-center">Your Sccore</v-card-title>
        <v-card-title class="text-center">Your Got <span class="text-red px-4">{{ numberOfCorrectAnswer }} / {{ ques }} </span>Correct Answer</v-card-title>
        <v-card-text class="text-center pa-0 my-5">
            <h1 class="bg-red py-4">{{ Sccore }} Point</h1>
        </v-card-text>
        <v-card-actions class="d-flex justify-center">
            <v-btn variant="tonal" color="orange" to="/">Play Again</v-btn>
        </v-card-actions>
        
    </v-card>
</template>

<script>
    export default {
        props:['numberOfCorrectAnswer','ques','Sccore']
    }
</script>