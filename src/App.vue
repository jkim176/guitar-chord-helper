<template>
  <div id="app">
    <Picker></Picker>
    <ChordDisplay></ChordDisplay>
  </div>
</template>

<script>
import Picker from './components/Picker.vue';
import ChordDisplay from './components/ChordDisplay.vue';

export default {
  name: 'app',
  components: {
    Picker,
    ChordDisplay
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
