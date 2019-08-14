<template>
  <div id="app">
    <Picker @send-musical-key-to-root="updateMusicalKey"
            @send-chord-type-to-root="updateChordType"
            :musical-key="musicalKey"
            :chord-type="chordType"
    >
    </Picker>

    <ChordDisplay :musical-key="musicalKey"
                  :chord-type="chordType"
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
  data() {
    return {
      musicalKey: "A",
      chordType: "Major"
    }
  },
  methods: {
    updateMusicalKey(newMusicalKey) {
      this.musicalKey = newMusicalKey;
    },
    updateChordType(newChordType) {
      this.chordType = newChordType;
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
