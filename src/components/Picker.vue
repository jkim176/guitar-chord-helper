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
      </select>
    </div>

    <div>
      <button id="previousChordArrayIndexButton"
              @click="decreaseChordArrayIndex"
              v-show="chordArrayIndex > 0"
      >
        &lt
      </button>
      <button id="nextChordArrayIndexButton"
              @click="increaseChordArrayIndex"
              v-show="chordArrayIndex < chordArray.length - 1"
      >
        &gt
      </button>
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
    },
    chordArray: {
      type: Array,
      required: true
    },
    chordArrayIndex: {
      type: Number,
      required: true
    }
  },
  methods: {
    sendMusicalKeyToRoot(event) {
      this.$emit('send-musical-key-to-root', event.target.value);
    },
    sendChordTypeToRoot(event) {
      this.$emit('send-chord-type-to-root', event.target.value);
    },
    decreaseChordArrayIndex() {
      if(this.chordArrayIndex > 0) {
        let newIndex = this.chordArrayIndex - 1;
        this.$emit('decrease-chord-array-index', newIndex);
      }
    },
    increaseChordArrayIndex() {
      if(this.chordArrayIndex < this.chordArray.length - 1) {
        let newIndex = this.chordArrayIndex + 1;
        this.$emit('increase-chord-array-index', newIndex);
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
