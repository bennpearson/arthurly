<template>
  <div class="question" v-bind:class="{ active: isActive }">
    <fieldset>
      <legend>What is your quest?</legend>
      <input type="checkbox" id="q2a1" value="grail" v-model="checkedNames">
      <label for="q2a1">To seek the Holy Grail</label>
      <input type="checkbox" id="q2a2" value="coconut" v-model="checkedNames">
      <label for="q2a2">To find a coconut</label>
      <input type="checkbox" id="q2a3" value="recruitment" v-model="checkedNames">
      <label for="q2a3">Recruitment</label>
      <br>
    </fieldset>
    <span>Checked names: {{ checkedNames }}</span>
    <button>Submit</button>
  </div>
</template>

<script>
export default {
  name: 'QuestionTwo',
  data: function() {
    return {
      isActive: false,
      checkedNames: []
    }
  }
}
</script>
