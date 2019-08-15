<template>
  <div class="chord-display">

    <div class="chord-label">
    </div>

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
           :class="{blank: firstString[index].marker == 0,
                    circle: firstString[index].marker == 1,
                    cross: firstString[index].marker == 2}"
           >
      </div>
    </div>

    <div class="string-container mid-string">
      <div v-for="(fret, index) in secondString"
           :key="fret.cellId"
           class="fret"
           :class="{blank: secondString[index].marker == 0,
                    circle: secondString[index].marker == 1,
                    cross: secondString[index].marker == 2}"
           >
      </div>
    </div>

    <div class="string-container mid-string">
      <div v-for="(fret, index) in thirdString"
           :key="fret.cellId"
           class="fret"
           :class="{blank: thirdString[index].marker == 0,
                    circle: thirdString[index].marker == 1,
                    cross: thirdString[index].marker == 2}"
           >
      </div>
    </div>

    <div class="string-container mid-string">
      <div v-for="(fret, index) in fourthString"
           :key="fret.cellId"
           class="fret"
           :class="{blank: fourthString[index].marker == 0,
                    circle: fourthString[index].marker == 1,
                    cross: fourthString[index].marker == 2}"
           >
      </div>
    </div>

    <div class="string-container mid-string">
      <div v-for="(fret, index) in fifthString"
           :key="fret.cellId"
           class="fret"
           :class="{blank: fifthString[index].marker == 0,
                    circle: fifthString[index].marker == 1,
                    cross: fifthString[index].marker == 2}"
           >
      </div>
    </div>

    <div class="string-container bot-string">
      <div v-for="(fret, index) in sixthString"
           :key="fret.cellId"
           class="fret"
           :class="{blank: sixthString[index].marker == 0,
                    circle: sixthString[index].marker == 1,
                    cross: sixthString[index].marker == 2}"
           >
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
  data() {
    return {
      fretLabels: [
        {
          labelId: "label0",
          label: 1
        },
        {
          labelId: "label1",
          label: 2
        },
        {
          labelId: "label2",
          label: 3
        },
        {
          labelId: "label3",
          label: 4
        },
        {
          labelId: "label4",
          label: 5
        },
        {
          labelId: "label5",
          label: 6
        }
      ],
      firstString: [  // marker 0,1,2 = (blank),circle,cross
        {
          cellId: 0,
          marker: 0
        },
        {
          cellId: 1,
          marker: 0
        },
        {
          cellId: 2,
          marker: 0
        },
        {
          cellId: 3,
          marker: 0
        },
        {
          cellId: 4,
          marker: 0
        },
        {
          cellId: 5,
          marker: 0
        },
      ],
      secondString: [
        {
          cellId: 10,
          marker: 0
        },
        {
          cellId: 11,
          marker: 1
        },
        {
          cellId: 12,
          marker: 0
        },
        {
          cellId: 13,
          marker: 0
        },
        {
          cellId: 14,
          marker: 0
        },
        {
          cellId: 15,
          marker: 0
        },
      ],
      thirdString: [
        {
          cellId: 20,
          marker: 0
        },
        {
          cellId: 21,
          marker: 1
        },
        {
          cellId: 22,
          marker: 0
        },
        {
          cellId: 23,
          marker: 0
        },
        {
          cellId: 24,
          marker: 0
        },
        {
          cellId: 25,
          marker: 0
        },
      ],
      fourthString: [
        {
          cellId: 30,
          marker: 0
        },
        {
          cellId: 31,
          marker: 1
        },
        {
          cellId: 32,
          marker: 0
        },
        {
          cellId: 33,
          marker: 0
        },
        {
          cellId: 34,
          marker: 0
        },
        {
          cellId: 35,
          marker: 0
        },
      ],
      fifthString: [
        {
          cellId: 40,
          marker: 0
        },
        {
          cellId: 41,
          marker: 0
        },
        {
          cellId: 42,
          marker: 0
        },
        {
          cellId: 43,
          marker: 0
        },
        {
          cellId: 44,
          marker: 0
        },
        {
          cellId: 45,
          marker: 0
        },
      ],
      sixthString: [
        {
          cellId: 50,
          marker: 0
        },
        {
          cellId: 51,
          marker: 0
        },
        {
          cellId: 52,
          marker: 0
        },
        {
          cellId: 53,
          marker: 0
        },
        {
          cellId: 54,
          marker: 0
        },
        {
          cellId: 55,
          marker: 0
        },
      ]
    }
  },
  props: {
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
    setFretLabels(chordArray, chordArrayIndex) {
      for(let i = 0; i < this.fretLabels.length; i++) {
        this.fretLabels[i].label = chordArray[chordArrayIndex].startingFret + i;
      }
    },
    setMarkers(chordArray, chordArrayIndex) {
      for(let i = 0; i < this.firstString.length; i++) {
        this.firstString[i].marker = chordArray[chordArrayIndex].chordPattern.firstString[i];
        this.secondString[i].marker = chordArray[chordArrayIndex].chordPattern.secondString[i];
        this.thirdString[i].marker = chordArray[chordArrayIndex].chordPattern.thirdString[i];
        this.fourthString[i].marker = chordArray[chordArrayIndex].chordPattern.fourthString[i];
        this.fifthString[i].marker = chordArray[chordArrayIndex].chordPattern.fifthString[i];
        this.sixthString[i].marker = chordArray[chordArrayIndex].chordPattern.sixthString[i];
      }
    },
  },
  watch: {
    chordArray(newVal, oldVal) {
      this.setFretLabels(newVal, this.chordArrayIndex);
      this.setMarkers(newVal, this.chordArrayIndex);
    },
    chordArrayIndex(newVal, oldVal) {
      this.setFretLabels(this.chordArray, newVal);
      this.setMarkers(this.chordArray, newVal);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.chord-display {
  display: flex;
  flex-direction: column;
}
.chord-label {

}
.fret-label-container {
  display: flex;
  flex: 1;
}
.fret-label {
  flex: 1;
  justify-content: space-between;
}
.string-container {
  display:flex;
  flex: 1;
  /* TODO: horizontal line aka the string */
}
.top-string {

}
.mid-string {

}
.bot-string {

}
.first-fret {

}
.mid-fret {

}
.last-fret {

}
.fret {
  flex: 1;
}
.blank {

}
.circle {
  width: 5px;
  height: 100px;
  background: black;
  border-radius: 50%;
}
.cross {

}
</style>
