<template>
  <div class="picker">

    <div>
      <label for="musicalKey">Key:</label>
      <select id="musicalKey"
              v-model="musicalKey"
              @change="changeMusicalKey"
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
      <label>
        Major
        <input type="radio"
               value="major"
               v-model="majorMinor"
               @change="changeMajorMinor"
               />
      </label>

      <label>
        Minor
        <input type="radio"
               value="minor"
               v-model="majorMinor"
               @change="changeMajorMinor"
               />
      </label>
    </div>

    <div>
      <!-- TODO embellishments -->
    </div>

  </div>
</template>

<script>
export default {
  name: "Picker",
  data() {
    return {
      musicalKey: "A",
      majorMinor: "major",
      embellishments: []
    }
  },
  methods: {
    changeMajorMinor() {
      let selectedMajorMinor = this.majorMinor;
      this.$root.$emit('change-major-minor', selectedMajorMinor);
    },
    changeMusicalKey() {
      let selectedMusicalKey = this.musicalKey;
      this.$root.$emit('change-musical-key', selectedMusicalKey);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
