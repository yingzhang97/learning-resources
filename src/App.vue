<template>
  <the-header title="Learning Resources"></the-header>
  <switch-buttons></switch-buttons>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import SwitchButtons from './components/learning-resources/SwitchButtons.vue';

export default {
  components: {
    TheHeader,
    SwitchButtons
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>