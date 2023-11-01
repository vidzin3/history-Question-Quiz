<template>
    <v-container fluid>
        <v-row>
            <v-col cols="12">
                <quizHeader :progress="progress" :questionCount="questionCount" v-for="quiz in data.quiz.filter(q => q.questions)" :quiz="quiz"/>
            </v-col>
            <v-col v-if="!show" cols="12">
                <quizBody v-for="quiz in data.quiz.map(q=>q.questions[currentQuestion])" 
                    :quiz="quiz"
                    @selectOption="countCorrect"
                    />
            </v-col>
            <v-col v-else cols="12">
                <result :Sccore="Sccore" :numberOfCorrectAnswer="numberOfCorrectAnswer" v-for="ques in data.quiz.map(q => q.questions.length)" :ques="ques" />
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    import { computed, ref } from 'vue';
    import quizBody from '../components/quizBody.vue';
    import quizHeader from '../components/quizHeader.vue';
    import result from '../components/result.vue'
    import data from '../data/db.json'
    
    export default {
        components:{
            quizBody,
            quizHeader,
            result
        },
        setup(){
            const currentQuestion = ref(0)
            const numberOfCorrectAnswer = ref(0)
            const show = ref(false)

            const questionCount = computed(()=>{
                return `${currentQuestion.value} / ${data.quiz.map(q => q.questions.length)}`
            })
            const progress = computed(() =>{
                const progressSize = currentQuestion.value/data.quiz.map(q => q.questions.length)*100
                return progressSize.toFixed(0)
            })
            const Sccore = computed(()=>{
                const progressSize = numberOfCorrectAnswer.value/data.quiz.map(q => q.questions.length)*100
                return progressSize.toFixed(2)
            })

            const countCorrect = (isCorrect) =>{
                if(isCorrect){
                    numberOfCorrectAnswer.value++
                }
                if(data.quiz.map(a=>a.questions.length) -1 === currentQuestion.value){
                    show.value = true
                }
                currentQuestion.value++
            }

            return {
                data,
                progress,
                questionCount,
                currentQuestion,
                countCorrect,
                numberOfCorrectAnswer,
                show,
                Sccore
            }
        }
    }
</script>