<template>
  <div class="picker">

    <div>
      <label for="musicalKey">Key</label>
      <select id="musicalKey"
              v-model="musicalKey"
              >
        <option>A</option>
        <option>A#</option>
        <option>B</option>
        <option>C</option>
        <option>C#</option>
        <option>D</option>
        <option>D#</option>
        <option>E</option>
        <option>F</option>
        <option>F#</option>
        <option>G</option>
        <option>G#</option>
      </select>
    </div>

    <div>
      <label for="chordType">Chords</label>
      <select id="chordType"
              v-model="chordType"
              >
        <option>Major</option>
        <option>Minor</option>
      </select>
    </div>

    <button id="getChordButton"
            @click="sendChordToDisplay"
            >
            Get
    </button>
  </div>
</template>

<script>
export default {
  name: "Picker",
  data() {
    return {
      musicalKey: "A",
      chordType: "Major"
    }
  },
  methods: {
    sendChordToDisplay() {
      let selectedChordType = this.chordType;
      let selectedMusicalKey = this.musicalKey;
      let chordKeyObject = {
        chordType: selectedChordType,
        musicalKey: selectedMusicalKey
      };
      this.$root.$emit('send-chord-to-display', chordKeyObject);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
