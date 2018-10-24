<template>
  <div class="question" v-bind:class="{ active: isActive }">
    <textarea v-model="questionasked" />
    <span>Picked names: {{ questionasked }}</span>
    <button>Submit</button>
  </div>
</template>

<script>
export default {
  name: 'QuestionThree',
  data: function() {
    return {
      isActive: false,
      questionasked: []
    }
  }
}
</script>