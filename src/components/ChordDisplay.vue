<template>
  <div class="chord-display">

    <div class="fret-label-container">
      <div v-for="(fret, index) in fretLabels"
           :key="fret.labelId"
           class="fret-label"
      >
           {{ fret.label }}
      </div>
    </div>

    <div class="string-container top-string">
      <div v-for="(fret, index) in firstString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: firstString[index].marker == 1,
                    cross: firstString[index].marker == 2}"
      >
        <div class="string">
        </div>
      </div>
    </div>

    <div class="string-container">
      <div v-for="(fret, index) in secondString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: secondString[index].marker == 1,
                    cross: secondString[index].marker == 2}"
      >
        <div class="string">
        </div>
      </div>
    </div>

    <div class="string-container">
      <div v-for="(fret, index) in thirdString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: thirdString[index].marker == 1,
                    cross: thirdString[index].marker == 2}"
      >
        <div class="string">
        </div>
      </div>
    </div>

    <div class="string-container">
      <div v-for="(fret, index) in fourthString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: fourthString[index].marker == 1,
                    cross: fourthString[index].marker == 2}"
      >
        <div class="string">
        </div>
      </div>
    </div>

    <div class="string-container">
      <div v-for="(fret, index) in fifthString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: fifthString[index].marker == 1,
                    cross: fifthString[index].marker == 2}"
      >
        <div class="string">
        </div>
      </div>
    </div>

    <div class="string-container bot-string">
      <div v-for="(fret, index) in sixthString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: sixthString[index].marker == 1,
                    cross: sixthString[index].marker == 2}"
      >
        <div class="string">
        </div>
      </div>
    </div>

  </div>
</template>

<script>


/*
function MajorBarre(){
  return {
    firstString:[],
    secondString:[],
    thirdString:[],
    fourthString:[],
    fifthString:[],
    sixthString:[],
  }
}

const Chords = {
  'E':{
    'Major':{
      chords:MajorBarre(),
      fretLabels:{}
    }
  }
}
*/

export default {
  name: "ChordDisplay",
  props: {
    chordArray: {
      type: Array,
      required: true
    },
    chordArrayIndex: {
      type: Number,
      required: true
    },
    fretLabels: {
      type: Array,
      required: true
    },
    firstString: {
      type: Array,
      required: true
    },
    secondString: {
      type: Array,
      required: true
    },
    thirdString: {
      type: Array,
      required: true
    },
    fourthString: {
      type: Array,
      required: true
    },
    fifthString: {
      type: Array,
      required: true
    },
    sixthString: {
      type: Array,
      required: true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.chord-display {
  display: flex;
  flex-direction: column;
}
.fret-label-container {
  display: flex;
  flex: 1 1 50px;
}
.fret-label {
  flex: 1;
  justify-content: space-between;
  /* could change to flex-end */
}
.string-container {
  display: flex;
  flex: 1 1 50px;
  /* TODO: horizontal line aka the string
  border-left: 1px solid black;
  border-right: 1px solid black;
  */
  border-left: 5px solid silver;
}
.top-string {
  border-top: 1px solid black;
}
.mid-string {

}
.bot-string {
  border-bottom: 1px solid black;
}
.first-fret {
  border-left: 5px solid silver;
}
.mid-fret {

}
.last-fret {

}
.fret {
  flex: 1 1 50px;
  /* */
  display: flex;
  border-right: 5px solid silver;
}
.circle {
  background: black;
  border-radius: 50%;
}
.cross {
  /* TODO: not implemented */
  background: red;
  border-radius: 50%;
}
.string {
  flex: 1 1 0;
  border-bottom: 2px solid black;
  height: 50%;
}
</style>
