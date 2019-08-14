<template>
  <div class="picker">

    <div>
      <label for="musicalKey">Key</label>
      <select id="musicalKey"
              @change="sendMusicalKeyToRoot($event)"
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
              @change="sendChordTypeToRoot($event)"
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
  props: {
    musicalKey: {
      type: String,
      required: true
    },
    chordType: {
      type: String,
      required: true
    }
  },
  methods: {
    sendMusicalKeyToRoot(event) {
      this.$emit('send-musical-key-to-root', event.target.value);
    },
    sendChordTypeToRoot(event) {
      this.$emit('send-chord-type-to-root', event.target.value);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
