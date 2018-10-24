<template>
  <input v-model="checkedNames"/>
</template>

<script>
export default {
  name: 'Checkbox',
  data: function() {
    return {
      checkedNames: []
    }
  }
}
</script>


