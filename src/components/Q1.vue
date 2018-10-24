<template>
  <div class="hello">
    <fieldset>
      <legend>{{question}}</legend>
      <div 
        v-for="answer in answers"
        v-bind:key="answer.id"
      >
        <label>{{answer}}</label>
        <input type="checkbox"/>
      </div>
    </fieldset>
  </div>
</template>

<script>
export default {
  name: 'Q1',
  data: function() {
    return {
      question: 'WHAT! Question 1',
      answers: ['answer 1', 'answer 2', 'answer 3', 'wrong answer']
    }
  }
}
</script>
