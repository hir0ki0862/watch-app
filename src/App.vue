<template>
  <div id="app">
    <Watch class="watch"></Watch>
  </div>
</template>

<script>
import Watch from '@/components/Watch';

export default {
  name: 'App',
  components: {
    Watch
  }
};
</script>

<style scoped>
.watch {
  width: 80vw;
  max-width: 700px;
  margin: 30px auto;
}
</style>

<style>
html {
  width: 100%;
  font-size: 62.5%;
}

body {
  margin: 0;
}

p {
  margin: 0;
}
</style>
