<template>
  <div id="app">
    <Generator />
  </div>
</template>

<script>
  import Generator from './components/Generator.vue';
  export default {
    name: 'App',
    components: {
      Generator,
    },
  };
</script>

<style>
  * {
    margin: 0;
    padding: 0;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    line-height: 1.6;
  }
  *:before,
  *:after {
    margin: 0;
    padding: 0;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    line-height: 1.6;
  }
  html {
    scroll-behavior: smooth;
  }
  body,
  html {
    height: 100%;
    padding-top: 0;
    width: 100%;
    font-family: 'Open Sans', sans-serif;
  }
</style>
