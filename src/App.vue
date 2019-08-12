<template>
  <div id="app">
    <Picker @send-chord-to-root="sendChordToDisplay"></Picker>
    <ChordDisplay :propMusicalKey="musicalKey"
                  :propChordTypechordType="chordType"
                  >
    </ChordDisplay>
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
  },
  data: {
    musicalKey: "A",
    chordType: "Major"
  },
  methods: {
    sendChordToDisplay(chordKeyObject) {
      this.musicalKey = chordKeyObject.musicalKey;
      this.chordType = chordKeyObject.chordType;
    }
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
