<template>
  <input v-bind:type="type" />
</template>

<script>
export default {
  name: 'Radio',
  props: {
    type: String
  }
}
</script>


