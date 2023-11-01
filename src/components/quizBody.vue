<template>
    <v-card class="pa-4" :elevation="4">
        <v-card-text class="text-center font-weight-bold text-subtitle-1">{{ quiz.text }}</v-card-text>
        <v-card-actions v-for="btn in quiz.options" :key="btn.id">
            <v-btn variant="tonal" block class="text-subtitle-1 text-blue" :elevation="3"
            @click="selectEmit(btn.isCorrect)"
            :ripple="rippleClass(btn.isCorrect)"
            >{{ btn.text }}</v-btn>
        </v-card-actions>
        <v-snackbar
        v-model="snackbar"
        :timeout="timeout"
        >
        {{ trueQues }}
        <template v-slot:actions>
            <v-btn @click="onClick">Close</v-btn>
        </template>
        </v-snackbar>
    </v-card>
</template>

<script setup>
    import {defineEmits, ref} from 'vue'
    const snackbar = ref(false)
    const trueQues = ref("");
    const emit = defineEmits('selectOption')
    const selectEmit = (isCorrect) =>{
        emit('selectOption',isCorrect)
        if(isCorrect){
            trueQues.value = "ត្រូវ"
        }else{
            trueQues.value = "ខុស"
        }
        snackbar.value = !snackbar.value
    }

    const onClick = () =>{
        snackbar.value = false
    }
    const rippleClass = (isCorrect) =>{
        return isCorrect ? { class: 'text-green-accent-3' } : { class: 'text-red-accent-4' };
    }
</script>
<script>
    export default {
        props:['quiz'],
        data(){
            return {
                timeout: 600,
            }
        }
    }
</script>