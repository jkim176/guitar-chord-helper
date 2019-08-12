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
           :class="{circle: firstString[index].marker == 1}"
           >
      </div>
    </div>

    <div class="string-container mid-string">
      <div v-for="(fret, index) in secondString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: secondString[index].marker == 1}"
           >
      </div>
    </div>

    <div class="string-container mid-string">
      <div v-for="(fret, index) in thirdString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: thirdString[index].marker == 1}"
           >
      </div>
    </div>

    <div class="string-container mid-string">
      <div v-for="(fret, index) in fourthString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: fourthString[index].marker == 1}"
           >
      </div>
    </div>

    <div class="string-container mid-string">
      <div v-for="(fret, index) in fifthString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: fifthString[index].marker == 1}"
           >
      </div>
    </div>

    <div class="string-container bot-string">
      <div v-for="(fret, index) in sixthString"
           :key="fret.cellId"
           class="fret"
           :class="{circle: sixthString[index].marker == 1}"
           >
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "ChordDisplay",
  data() {
    return {
      fretLabels: [
        {
          labelId: "label0",
          label: 4
        },
        {
          labelId: "label1",
          label: 5
        },
        {
          labelId: "label2",
          label: 6
        },
        {
          labelId: "label3",
          label: 7
        },
        {
          labelId: "label4",
          label: 8
        },
        {
          labelId: "label5",
          label: 9
        }
      ],
      firstString: [  // marker 0,1,2 = (blank),circle,cross
        {
          cellId: 0,
          marker: 1
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
          marker: 1
        },
        {
          cellId: 11,
          marker: 0
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
          marker: 0
        },
        {
          cellId: 32,
          marker: 1
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
          marker: 1
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
          marker: 1
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
      ],
      major: [
        {
          firstString: [1, 0, 0, 0, 0, 0],
          secondString: [1, 0, 0, 0, 0, 0],
          thirdString: [0, 1, 0, 0, 0, 0],
          fourthString: [0, 0, 1, 0, 0, 0],
          fifthString: [0, 0, 1, 0, 0, 0],
          sixthString: [1, 0, 0, 0, 0, 0]
        },
      ],
      minor: [
        {
          firstString: [1, 0, 0, 0, 0, 0],
          secondString: [1, 0, 0, 0, 0, 0],
          thirdString: [1, 0, 0, 0, 0, 0],
          fourthString: [0, 0, 1, 0, 0, 0],
          fifthString: [0, 0, 1, 0, 0, 0],
          sixthString: [1, 0, 0, 0, 0, 0]
        },
      ],
    }
  },
  methods: {

  },
  props: {
    propMusicalKey: {
      type: String,
      required: true
    },
    propChordType: {
      type: String,
      required: true
    }
  },

  /*
  computed: {
    setChordDisplay() { // initializes display to type[0] ... change variation index with buttons
      // set string labels
      if(this.musicalKey == "F") {
        this.startingFret = 0;
      } else if(this.musicalKey == "F#") {
        this.startingFret = 1;
      } else if(this.musicalKey == "G") {
        this.startingFret = 2;
      } else if(this.musicalKey == "G#") {
        this.startingFret = 3;
      } else if(this.musicalKey == "A") {
        this.startingFret = 4;
      } else if(this.musicalKey == "A#") {
        this.startingFret = 5;
      } else if(this.musicalKey == "B") {
        this.startingFret = 6;
      } else if(this.musicalKey == "C") {
        this.startingFret = 7;
      } else if(this.musicalKey == "C#") {
        this.startingFret = 8;
      } else if(this.musicalKey == "D") {
        this.startingFret = 9;
      } else if(this.musicalKey == "D#") {
        this.startingFret = 10;
      } else {
        this.startingFret = 0;
      }
      for(let i = 0; i < this.fretLabels.length; i++) {
        this.fretLabels[i].label = this.startingFret + i;
      }
      // set markers
      if((this.chordType == "Major" || this.chordType == "Minor") && this.musicalKey == "E") {

      }
      else if(this.chordType == "Major") {
        for(let i = 0; i < this.firstString.length; i++) {
          this.firstString[i].marker = this.major[0].firstString[i];
          this.secondString[i].marker = this.major[0].secondString[i];
          this.thirdString[i].marker = this.major[0].thirdString[i];
          this.fourthString[i].marker = this.major[0].fourthString[i];
          this.fifthString[i].marker = this.major[0].fifthString[i];
          this.sixthString[i].marker = this.major[0].sixthString[i];
        }
      } else if(this.chordType == "Minor") {
        for(let i = 0; i < this.firstString.length; i++) {
          this.firstString[i].marker = this.minor[0].firstString[i];
          this.secondString[i].marker = this.minor[0].secondString[i];
          this.thirdString[i].marker = this.minor[0].thirdString[i];
          this.fourthString[i].marker = this.minor[0].fourthString[i];
          this.fifthString[i].marker = this.minor[0].fifthString[i];
          this.sixthString[i].marker = this.minor[0].sixthString[i];
        }
      }
    }
  }
  */

  /*
  mounted() {
    this.$root.$on('send-chord-to-display', chordKeyObject => {
      let chordType = chordKeyObject.chordType;
      let musicalKey = chordKeyObject.musicalKey;
      // cannot call method from mounted
      if(chordKeyObject.chordType == "Major") {
        for(let i = 0; i < this.firstString.length; i++) {
          this.firstString[i].marker = this.major.firstString[i];
          this.secondString[i].marker = this.major.secondString[i];
          this.thirdString[i].marker = this.major.thirdString[i];
          this.fourthString[i].marker = this.major.fourthString[i];
          this.fifthString[i].marker = this.major.fifthString[i];
          this.sixthString[i].marker = this.major.sixthString[i];
        }
      } else if(chordKeyObject.chordType == "Minor") {
        for(let i = 0; i < this.firstString.length; i++) {
          this.firstString[i].marker = this.minor.firstString[i];
          this.secondString[i].marker = this.minor.secondString[i];
          this.thirdString[i].marker = this.minor.thirdString[i];
          this.fourthString[i].marker = this.minor.fourthString[i];
          this.fifthString[i].marker = this.minor.fifthString[i];
          this.sixthString[i].marker = this.minor.sixthString[i];
        }
      }
      // TODO: frets based on variations
      let startingFret;
      switch(chordKeyObject.musicalKey) {
          case "F":
            startingFret = 0;
            break;
          case "F#":
            startingFret = 1;
            break;
          case "G":
            startingFret = 2;
            break;
          case "G#":
            startingFret = 3;
            break;
          case "A":
            startingFret = 4;
            break;
          case "A#":
            startingFret = 5;
            break;
          case "B":
            startingFret = 6;
            break;
          case "C":
            startingFret = 7;
            break;
          case "C#":
            startingFret = 8;
            break;
          case "D":
            startingFret = 9;
            break;
          case "D#":
            startingFret = 10;
            break;
      }
      for(let i = 0; i < this.fretLabels.length; i++) {
        this.fretLabels[i].label = startingFret + i;
      }
    });
  }
  */
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
.circle {
  width: 5px;
  height: 100px;
  background: black;
  border-radius: 50%;
}
.cross {

}
</style>
