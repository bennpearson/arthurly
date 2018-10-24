<template>
  <div id="app">
    <Intro title="Arthurly" text="Welcome intrepid knight"/>
    <QuestionOne/>
    <!-- <QuestionTwo/>
    <QuestionThree/> -->
    <!-- <form>
      <Giphy />
      <fieldset>
        <Legend text="WHAT is your name?"/>
        <Label text="My name is Sir Lancelot of Camelot" />
        <Radio type="radio"/>
        <Label text="Sir Robin of Camelot" />
        <Radio type="radio"/>
        <Label text="Sir Galahad of Camelot" />
        <Radio type="radio"/>
        <Label text="It is a Recruiter, King of the recruiters" />
        <Radio type="radio"/>
      </fieldset>

      <Giphy  />
      <fieldset>
        <Legend text="WHAT is your quest?"/>
        <Label for="q2a1" text="To seek the Holy Grail" />
        <Checkbox id="q2a1" type="checkbox" />
        <Label for="q2a2" text="I seek the Holy Grail" />
        <Checkbox id="q2a2" type="checkbox" />
        <Label for="q2a3" text="To find the Holy Grail" />
        <Checkbox id="q2a3" type="checkbox" />
        <Label for="q2a4" text="To Recruit the Holy Grail" />
        <Checkbox id="q2a4" type="checkbox" />
      </fieldset>

      <Giphy />
      <Label text="What is your Question?" />
      <Textarea />
    </form> -->
  </div>
</template>

<script>
import Intro from './components/Intro.vue'
import QuestionOne from './components/QuestionOne.vue'
import QuestionTwo from './components/QuestionTwo.vue'
import QuestionThree from './components/QuestionThree.vue'
import Checkbox from './components/forms/Checkbox.vue'
import Radio from './components/forms/Radio.vue'
import Label from './components/forms/Label.vue'
import Legend from './components/forms/Legend.vue'
import Textarea from './components/forms/Textarea.vue'
import Giphy from './components/Giphy.vue'

export default {
  name: 'app',
  components: {
    Intro,
    QuestionOne,
    QuestionTwo,
    QuestionThree,
    Checkbox,
    Radio,
    Label,
    Legend,
    Textarea,
    Giphy
  }
}


</script>

<style>
html {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #fff;
  background: black;
}

body {
  margin: 0;
}

</style>
