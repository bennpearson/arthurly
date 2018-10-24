<template>
  <div class="intro">
    <h1 class="title">
      <img class="logo" alt="Arthurly" src="/images/logo.png"> {{ title }}
    </h1>
    <!-- <p>
      {{ text }}
    </p> -->
  </div>
</template>

<script>
export default {
  name: 'Intro',
  props: {
    title: String,
    text: String
  }
}
</script>

<style>

.intro {
  position: relative;
  padding: 40px;
  z-index: 2;
}

.title {
    font-size: 77px;
    letter-spacing: 7px;
    font-weight: 300;
    margin: 0;
}

.logo {
  width: 150px;
  vertical-align: middle;
}
</style>

