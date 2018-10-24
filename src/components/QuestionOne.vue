<template>
<div class="questions">
    <div class="question question--start" v-bind:class="{ active: isActiveStart }">
    <div class="question__va">
      <fieldset>
        <legend>STOP!</legend>
        <h2>Who would cross the Bridge of Death must answer me these questions three, ere the other side he see.</h2>
        <button v-on:click="nextQuestionStart">Begin</button>
      </fieldset>
    </div>
  </div>
  <div class="question question--one" v-bind:class="{ active: isActive }">
    <div class="question__va">
      <fieldset>
        <legend>WHAT is your name?</legend>
        <div class="radio__item">
          <input type="radio" id="q1a1" value="lancelot" v-model="picked">
          <label for="q1a1">My name is Sir Lancelot of Camelot</label>
        </div>
        <div class="radio__item">
          <input type="radio" id="q1a2" value="galahad" v-model="picked">
          <label for="q1a2">Sir Galahad of Camelot</label>
        </div>
        <div class="radio__item">
          <input type="radio" id="q1a3" value="recruitment" v-model="picked">
          <label for="q1a3">I'm a recruiter</label>
        </div>
        <br>
        <button v-on:click="nextQuestion">Submit</button>
      </fieldset>
    </div>
  </div>
  <div class="question question--two" v-bind:class="{ active: isActiveQ2 }">
    <div class="question__va">
      <fieldset>
        <legend>WHAT is your quest?</legend>
        <div class="checkboxes__item">
          <input type="checkbox" id="q2a1" value="grail" v-model="checkedNames">
          <label for="q2a1">To seek the Holy Grail</label>
        </div>
        <div class="checkboxes__item">
          <input type="checkbox" id="q2a2" value="coconut" v-model="checkedNames">
          <label for="q2a2">To find a coconut</label>
        </div>
        <div class="checkboxes__item">
          <input type="checkbox" id="q2a3" value="recruitment" v-model="checkedNames">
          <label for="q2a3">Recruitment</label>
        </div>
        <br>
        <button v-on:click="nextQuestion2">Submit</button>
      </fieldset>
    </div>
  </div>
  <div class="question question--three" v-bind:class="{ active: isActiveQ3 }">
    <div class="question__va">
      <fieldset>
        <legend>WHAT is your question?</legend>
        <textarea v-model="questionasked" />
        <button v-on:click="nextQuestion3">Submit</button>
      </fieldset>
    </div>
  </div>
  <div class="question question--four" v-bind:class="{ active: isActiveGameOver }">
    <div class="question__va">
      <fieldset>
        <legend>Game Over</legend>
        <h2>You have failed. Add credits to play again</h2>
          <h2><button class="button button--secondary" v-on:click="count++">+</button> {{ count }} Credits. </h2>
          <div v-if="count < 1">
            <button v-on:click="nextQuestion4">Submit</button>
          </div>
          <div v-else>
            <button v-on:click="nextQuestion4(); count--">Submit</button>
          </div>
      </fieldset>
    </div>
  </div>
  <div class="question question--five" v-bind:class="{ active: isActiveComplete }">
    <div class="question__va">
      <fieldset>
        <legend>Complete</legend>
        <h2>Well done brave knight you shall cross the bridge of death.</h2>
        <button v-on:click="nextQuestion5">Play again</button>
      </fieldset>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'QuestionOne',
  data: function() {
    return {
      isActiveStart: true,
      isActive: false,
      isActiveQ2: false,
      isActiveQ3: false,
      isActiveGameOver: false,
      isActiveComplete: false,
      picked: [],
      checkedNames: [],
      questionasked: [],
      continues: [],
      playAgain: [],
      count: 0
    }
  },
  methods: {
    nextQuestionStart: function () {
      this.isActiveStart = false
      this.isActive = true
    },

    nextQuestion: function () {
      if( this.picked === 'recruitment' ) {
        this.isActive = false
        this.isActiveGameOver = true
      } else if ( this.picked.length !== 0 ) {
        this.isActive = false
        this.isActiveQ2 = true
      }
    },
    nextQuestion2: function () {
      if( this.checkedNames.indexOf('recruitment') > -1 ) {
        this.isActiveQ2 = false
        this.isActiveGameOver = true
      } else if ( this.checkedNames.length !== 0 ) {
        this.isActiveQ2 = false
        this.isActiveQ3 = true
      }
    },
    nextQuestion3: function () {
      if( this.questionasked.indexOf('recruitment') > -1 ) {
        this.isActiveQ3 = false
        this.isActiveGameOver = true
      } else if ( this.questionasked.length !== 0 ) {
        this.isActiveQ3 = false
        this.isActiveComplete = true
      }
    },
    nextQuestion4: function () {
      if( this.count > 0 ) {
        this.isActive = true
        this.isActiveGameOver = false
      }
    },
    nextQuestion5: function () {
      this.isActive = true
      this.isActiveComplete = false
    }
  }
}
</script>


<style>

.question {
  opacity: 0;
  transition: opacity 1s ease-in-out;
}

.question.active {
  opacity: 1;
}

.question:before {
  content: '';
  display: block;
  width: 100%;
  height: 100vh;
  background-color: black;
  opacity: 0.7;
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
}

.question::after {
  content: '';
  display: block;
  position: absolute;
  width: 100%;
  height: 100vh;
  background-color: black;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  top: 0;
  left: 0;
}


.question--start:after {
  background-image: url('/images/q1.gif');
}

.question--one:after {
  background-image: url('/images/q1.gif');
}

.question--two:after {
  background-image: url('/images/q2.gif');
}

.question--three:after {
  background-image: url('/images/q3.gif');
}

.question--four:after {
  background-image: url('/images/gameover.gif');
}

.question--five:after {
  background-image: url('/images/completed.gif');
}

.question__va {
  position: relative;
  z-index: 1;
}

fieldset {
  border: 0;
  z-index: 2;
  padding: 40px;
  position: absolute;
  max-width: 500px;
}

legend {
  font-size: 45px;
  font-weight: 700;
}

h2 {
  margin-top: 0;
}

.checkboxes__item {
  font-family: "nta",Arial,sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  position: relative;
  min-height: 40px;
  margin-bottom: 10px;
  padding: 0 0 0 40px;
  clear: left;
}

.checkboxes__item input{
  position: absolute;
  z-index: 1;
  top: 0;
  left: 0;
  width: 40px;
  height: 40px;
  cursor: pointer;
  margin: 0;
  opacity: 0;
}

.checkboxes__item label {
    display: inline-block;
    margin-bottom: 0;
    padding: 8px 15px 5px;
    cursor: pointer;
    -ms-touch-action: manipulation;
    touch-action: manipulation;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-weight: 400;
    font-size: 21px;
    line-height: 1.25;
    display: block;
    margin-bottom: 5px;
}

.checkboxes__item input+label::before {
    content: "";
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    position: absolute;
    top: 0;
    left: 0;
    width: 40px;
    height: 40px;
    border: 2px solid currentColor;
    background: transparent;
}

.checkboxes__item input+label::after {
    content: "";
    position: absolute;
    top: 11px;
    left: 9px;
    width: 18px;
    height: 7px;
    -webkit-transform: rotate(-45deg);
    -ms-transform: rotate(-45deg);
    transform: rotate(-45deg);
    border: solid;
    border-width: 0 0 5px 5px;
    border-top-color: transparent;
    opacity: 0;
    background: transparent;
}

.checkboxes__item input:checked+label::after {
    opacity: 1;
}

.radio__item {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  position: relative;
  min-height: 40px;
  margin-bottom: 10px;
  padding: 0 0 0 40px;
  clear: left;
}

.radio__item input {
  position: absolute;
  z-index: 1;
  top: 0;
  left: 0;
  width: 40px;
  height: 40px;
  cursor: pointer;
  margin: 0;
  opacity: 0;
}

.radio__item label {
  display: inline-block;
    margin-bottom: 0;
    padding: 8px 15px 5px;
    cursor: pointer;
    -ms-touch-action: manipulation;
    touch-action: manipulation;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-weight: 400;
    font-size: 21px;
    line-height: 1.25;
    display: block;
    margin-bottom: 5px;
}

.radio__item input+label::before {
    content: "";
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    position: absolute;
    top: 0;
    left: 0;
    width: 40px;
    height: 40px;
    border: 2px solid currentColor;
    border-radius: 50%;
    background: transparent;
}

.radio__item input+label::after {
    content: "";
    position: absolute;
    top: 10px;
    left: 10px;
    width: 0;
    height: 0;
    border: 10px solid currentColor;
    border-radius: 50%;
    opacity: 0;
    background: currentColor;
}

.radio__item input:checked+label::after {
    opacity: 1;
}

button {
  display: block;
  padding: 10px 30px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-weight: 400;
  font-size: 26px;
  line-height: 1.1875;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  display: inline-block;
  position: relative;
  margin-top: 20px;
  margin-bottom: 20px;
  border: 2px solid white;
  border-radius: 0;
  color: #fff;
  background-color: transparent;
  -webkit-box-shadow: 0 2px 0 #003618;
  box-shadow: 0 2px 0 #003618;
  text-align: center;
  vertical-align: top;
  cursor: pointer;
  -webkit-appearance: none;
}

.button--secondary {
  border-radius: 100%;
  height: 50px;
  width: 50px;
  padding: 0;
  vertical-align: baseline;
  font-weight: bold;
  line-height: 10px;
  margin-right: 10px;
}

textarea {
  border: 1px solid white;
  background-color: transparent;
  color: white;
  display: block;
  width: 320px;
  height: 100px;
  margin-bottom: 30px;
  padding: 10px;
  font-size: 21px;
}
</style>