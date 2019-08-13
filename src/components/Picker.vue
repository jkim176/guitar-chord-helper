<template>
  <div class="picker">

    <div>
      <label for="musicalKey">Key</label>
      <select id="musicalKey"
              v-model="musicalKey"
              @change="sendChordToRoot"
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
              @change="sendChordToRoot"
              >
        <option>Major</option>
        <option>Minor</option>
        <option>7</option>
        <option>maj7</option>
        <option>m7</option>
        <option>m-maj7</option>
      </select>
    </div>

  </div>
</template>

<script>
export default {
  name: "Picker",
  data() {
    return {
      musicalKey: "F",
      chordType: "Major"
    }
  },
  methods: {
    sendChordToRoot() {
      let selectedChordType = this.chordType;
      let selectedMusicalKey = this.musicalKey;
      let chordKeyObject = {
        chordType: selectedChordType,
        musicalKey: selectedMusicalKey
      };
      this.$emit('send-chord-to-root', chordKeyObject);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
