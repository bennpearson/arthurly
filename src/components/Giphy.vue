<template>
  <div v-bind:class="{ active: isActive }">
  </div>
</template>

<script>
export default {
  name: 'Giphy',
  data: function() {
    return {
      isActive: false,
      hasError: false
    }
  },
  computed: {
      activeFormSection: function () {
          
      }
  }
}
</script>
