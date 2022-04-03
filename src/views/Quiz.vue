<template>
  <div class="quiz">
        

      <div class="flex items-center justify-center w-full h-screen">
            <div class="w-full max-w-xl">
                <h1 class="text-4xl font-bold text-center animate__animated animate__slow animate__zoomInDown">
                 Riddles
                </h1>
                <div class="quizzy w-full p-12 mt-8  rounded-lg shadow-lg">
                    <div v-if="index < count">
                        <p class="text-2xl font-bold ques">
                            {{ questions[index]['question'] }}
                        </p>
                        <label
                            :for="key"
                            class="block px-6 py-2 mt-4 text-lg border border-gray-300 rounded-lg bg-white"
                            v-for="answer,key in questions[index]['answers']" 
                            :class="{'hover:bg-gray-100 cursor-pointer' : selectedAnswer == ''},
                        {'bg-red-300 border border-20 border-red-400' : selectedAnswer == key},
                        {'bg-green-300  border border-10 border-green-400' : key == questions[index]['correctAnswer'] && selectedAnswer != ''}"
                        >
                            <input
                                type="radio"
                                :id="key"
                                class="hidden"
                                :value="key"
                                @change="answered($event)"
                                v-model="selectedAnswer"
                                :disabled="selectedAnswer != ''"
                            />
                            {{ answer }}
                        </label>
                        <div class="flow-root mt-6">
                            <button
                                class="float-right px-5 py-2 text-sm font-bold tracking-wide text-white nexy rounded-full"
                                v-show="selectedAnswer != '' && index < count-1"
                                @click="nextQuestion"
                            >
                                Next Question &gt;
                            </button>
                            <button
                                class="float-right px-5 py-2 text-sm font-bold tracking-wide text-white bg-indigo-900 rounded-full"
                                v-show="selectedAnswer != '' && index == count-1"
                                @click="showResults"
                            >
                                View Results
                            </button>
                        </div>
                    </div>
                    <div v-else>
                        <div class="results">
                        <h2 class="text-3xl font-bold">Your Score Result</h2>
                       <div v-html="message"></div>
                        <div class="flex justify-start mt-6 space-x-4">
                            <p>
                                Correct Answers:
                                <span class="text-2xl font-bold text-green-700"
                                    >{{ correctAnswer }}</span
                                >
                            </p>
                            <p>
                                Incorrect Answers:
                                <span class="text-2xl font-bold text-red-700"
                                    >{{ wrongAnswer }}</span
                                >
                            </p>
                        </div>
                        <div class="flow-root mt-6">
                            <button
                                class="float-right px-5 py-2 text-sm font-bold tracking-wide text-white bg-indigo-900 rounded-full"
                                @click="resetQuiz"
                            >
                                Start Over
                            </button>
                        </div>
                    </div>
                      </div>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
export default {
data(){
    return{
        index:0,
        message:"",
        selectedAnswer: '',
            correctAnswer: 0,
            wrongAnswer: 0,
            count: 10,
              questions: [
                {
                    question: "What has to be broken before you can use it?",
                    answers: {a: 'A promise', b: 'A spaceship', c: 'An egg', d: 'A horse'},
                    correctAnswer: 'c'
                },
                {
                    question: "What month of the year has 28 days?",
                    answers: {a: 'March', b: 'Febuary', c: 'October', d: 'All of them'},
                    correctAnswer: 'd'
                },
                {
                    question: "What is always in front of you but can not be seen?",
                    answers: {a: 'Spectacles', b: 'Future',c: 'Ghosts',d: 'Nose'},
                    correctAnswer: 'b'
                },
                  {
                    question: "What can you break, even if you never pick it up or touch it?",
                    answers: {a: 'Promise', b: 'Wind',c: 'Silence',d: 'Darkness'},
                    correctAnswer: 'a'
                },
                  {
                    question: "What gets wet while drying?",
                    answers: {a: 'Towel', b: 'Tears',c: 'Family',d: 'Darkness'},
                    correctAnswer: 'a'
                },
                  {
                    question: "What can you keep after giving to someone?",
                    answers: {a: 'Your word', b: 'Family',c: 'Darkness',d: 'Money'},
                    correctAnswer: 'a'
                },
                  {
                    question: "I shave every day, but my beard stays the same. What am I?",
                    answers: {a: 'Family', b: 'Eraser',c: 'Barber',d: 'Darkness'},
                    correctAnswer: 'c'
                },
                  {
                    question: "I have branches, but no fruit, trunk or leaves. What am I?",
                    answers: {a: 'Tree', b: 'Darkness',c: 'Elephant',d: 'Bank'},
                    correctAnswer: 'd'
                },
                  {
                    question: "The more of this there is, the less you see. What is it?",
                    answers: {a: 'Spectacles', b: 'Eyes',c: 'Family',d: 'Darkness'},
                    correctAnswer: 'd'
                },
                  {
                    question: "What has a head and a tail but no body?",
                    answers: {a: 'Dinosaur', b: 'Coin',c: 'Ghosts',d: 'Family'},
                    correctAnswer: 'b'
                },
            ] 
    }
},
  methods: {
        answered(e) {
            this.selectedAnswer = e.target.value
            if(this.selectedAnswer == this.questions[this.index]['correctAnswer'])
                this.correctAnswer++
            else
                this.wrongAnswer++
        },
        nextQuestion() {
            this.index++
            this.selectedAnswer = ''
        },
        showResults() {
            this.index++
           
           if(this.correctAnswer >=7){
                this.message=`<h1 style="color:green;">PASS</h1>`
            }
            else(this.message=`<h1 style="color:red;">FAIL</h1>`)
        },
        resetQuiz() {
            this.index = 0
            this.selectedAnswer = ''
            this.correctAnswer = 0
            this.wrongAnswer = 0
        }
    }
}
</script>

<style scoped>
.quiz{
  background:linear-gradient(0deg, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url("../assets/riddle.jpg");
    background-size: cover;
  height: 100vh;
  overflow-y: hidden !important;
}h1{
      color:  rgb(253, 81, 1);
}
.nexy{
    background-color: rgb(253, 81, 1) ;
    border: solid 2px white;
}
.quizzy{
    background: rgba( 253, 114, 0, 0.6 );
box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
backdrop-filter: blur( 4px );
-webkit-backdrop-filter: blur( 4px );
border-radius: 10px;
border: 1px solid rgba( 255, 255, 255, 0.18 );
}
.ques{
    color:whitesmoke !important;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}
@media only screen and (max-width:700px) {
    .quiz{
       padding-left: 5%;
       padding-right: 5%;
    }
}
</style> 