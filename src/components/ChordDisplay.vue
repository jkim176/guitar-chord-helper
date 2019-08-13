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
      /*
      blank: {
        firstString:  [0, 0, 0, 0, 0, 0],
        secondString: [0, 0, 0, 0, 0, 0],
        thirdString:  [0, 0, 0, 0, 0, 0],
        fourthString: [0, 0, 0, 0, 0, 0],
        fifthString:  [0, 0, 0, 0, 0, 0],
        sixthString:  [0, 0, 0, 0, 0, 0]
      },
      */
      majorBarre: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString:  [0, 1, 0, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString:  [0, 0, 1, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      majorBarre2: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [0, 0, 1, 0, 0, 0],
        thirdString:  [0, 0, 1, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString:  [1, 0, 0, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      minorBarre: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString:  [0, 0, 1, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      minorBarre2: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [0, 1, 0, 0, 0, 0],
        thirdString:  [0, 0, 1, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString:  [1, 0, 0, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      majorBarreMinor7: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString:  [0, 1, 0, 0, 0, 0],
        fourthString: [1, 0, 0, 0, 0, 0],
        fifthString:  [0, 0, 1, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      majorBarreMinor72: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [0, 0, 1, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString:  [1, 0, 0, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      majorBarreMajor7: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString:  [0, 1, 0, 0, 0, 0],
        fourthString: [0, 1, 0, 0, 0, 0],
        fifthString:  [0, 0, 1, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      majorBarreMajor72: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [0, 0, 1, 0, 0, 0],
        thirdString:  [0, 1, 0, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString:  [1, 0, 0, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      minorBarreMinor7: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [1, 0, 0, 0, 0, 0],
        fifthString:  [0, 0, 1, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      minorBarreMinor72: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [0, 1, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString:  [1, 0, 0, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      minorBarreMajor7: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [0, 1, 0, 0, 0, 0],
        fifthString:  [0, 0, 1, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      minorBarreMajor72: {
        firstString:  [1, 0, 0, 0, 0, 0],
        secondString: [0, 1, 0, 0, 0, 0],
        thirdString:  [0, 1, 0, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString:  [1, 0, 0, 0, 0, 0],
        sixthString:  [1, 0, 0, 0, 0, 0]
      },
      openEMajor: {
        firstString:  [0, 0, 0, 0, 0, 0],
        secondString: [0, 0, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [0, 1, 0, 0, 0, 0],
        fifthString:  [0, 1, 0, 0, 0, 0],
        sixthString:  [0, 0, 0, 0, 0, 0]
      },
      openEMinor: {
        firstString:  [0, 0, 0, 0, 0, 0],
        secondString: [0, 0, 0, 0, 0, 0],
        thirdString:  [0, 0, 0, 0, 0, 0],
        fourthString: [0, 1, 0, 0, 0, 0],
        fifthString:  [0, 1, 0, 0, 0, 0],
        sixthString:  [0, 0, 0, 0, 0, 0]
      },
      openEMajorMinor7: {
        firstString:  [0, 0, 0, 0, 0, 0],
        secondString: [0, 0, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [0, 0, 0, 0, 0, 0],
        fifthString:  [0, 1, 0, 0, 0, 0],
        sixthString:  [0, 0, 0, 0, 0, 0]
      },
      openEMajorMajor7: {
        firstString:  [0, 0, 0, 0, 0, 0],
        secondString: [0, 0, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [1, 0, 0, 0, 0, 0],
        fifthString:  [0, 1, 0, 0, 0, 0],
        sixthString:  [0, 0, 0, 0, 0, 0]
      },
      openEMinorMinor7: {
        firstString:  [0, 0, 0, 0, 0, 0],
        secondString: [0, 0, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [0, 0, 0, 0, 0, 0],
        fifthString:  [0, 1, 0, 0, 0, 0],
        sixthString:  [0, 0, 0, 0, 0, 0]
      },
      openEMinorMajor7: {
        firstString:  [0, 0, 0, 0, 0, 0],
        secondString: [0, 0, 0, 0, 0, 0],
        thirdString:  [1, 0, 0, 0, 0, 0],
        fourthString: [1, 0, 0, 0, 0, 0],
        fifthString:  [0, 1, 0, 0, 0, 0],
        sixthString:  [0, 0, 0, 0, 0, 0]
      },
    }
  },
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
    setFretLabels(startingFret) {
      for(let i = 0; i < this.fretLabels.length; i++) {
        this.fretLabels[i].label = startingFret + i;
      }
    },
    setMarkers(chordType) {
      for(let i = 0; i < this.firstString.length; i++) {
        this.firstString[i].marker = chordType.firstString[i];
        this.secondString[i].marker = chordType.secondString[i];
        this.thirdString[i].marker = chordType.thirdString[i];
        this.fourthString[i].marker = chordType.fourthString[i];
        this.fifthString[i].marker = chordType.fifthString[i];
        this.sixthString[i].marker = chordType.sixthString[i];
      }
    },
  },
  watch: {
    musicalKey(newVal, oldVal) {
      if(newVal == "E") {
        if(this.chordType == "Major") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMajor);
        } else if(this.chordType == "Minor") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMinor);
        } else if(this.chordType == "7") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMajorMinor7);
        } else if(this.chordType == "maj7") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMajorMajor7);
        } else if(this.chordType == "m7") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMinorMinor7);
        } else if(this.chordType == "m-maj7") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMinorMajor7);
        }
      } else if(newVal == "F") {
        if(this.chordType == "Major") {
          this.setFretLabels(1);
          this.setMarkers(this.majorBarre);
        } else if(this.chordType == "Minor") {
          this.setFretLabels(1);
          this.setMarkers(this.minorBarre);
        } else if(this.chordType == "7") {
          this.setFretLabels(1);
          this.setMarkers(this.majorBarreMinor7);
        } else if(this.chordType == "maj7") {
          this.setFretLabels(1);
          this.setMarkers(this.majorBarreMajor7);
        } else if(this.chordType == "m7") {
          this.setFretLabels(1);
          this.setMarkers(this.minorBarreMinor7);
        } else if(this.chordType == "m-maj7") {
          this.setFretLabels(1);
          this.setMarkers(this.minorBarreMajor7);
        }
      } else if(newVal == "F#") {

      } else if(newVal == "G") {

      } else if(newVal == "G#") {

      } else if(newVal == "A") {

      } else if(newVal == "A#") {

      } else if(newVal == "B") {

      } else if(newVal == "C") {

      } else if(newVal == "C#") {

      } else if(newVal == "D") {

      } else if(newVal == "D#") {

      }
    },
    chordType(newVal, oldVal) {
      if(this.musicalKey == "E") {
        if(newVal == "Major") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMajor);
        } else if(newVal == "Minor") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMinor);
        } else if(newVal == "7") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMajorMinor7);
        } else if(newVal == "maj7") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMajorMajor7);
        } else if(newVal == "m7") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMinorMinor7);
        } else if(newVal == "m-maj7") {
          this.setFretLabels(1);
          this.setMarkers(this.openEMinorMajor7);
        }
      } else if(this.musicalKey == "F") {
        if(newVal == "Major") {
          this.setFretLabels(1);
          this.setMarkers(this.majorBarre);
        } else if(newVal == "Minor") {
          this.setFretLabels(1);
          this.setMarkers(this.minorBarre);
        } else if(newVal == "7") {
          this.setFretLabels(1);
          this.setMarkers(this.majorBarreMinor7);
        } else if(newVal == "maj7") {
          this.setFretLabels(1);
          this.setMarkers(this.majorBarreMajor7);
        } else if(newVal == "m7") {
          this.setFretLabels(1);
          this.setMarkers(this.minorBarreMinor7);
        } else if(newVal == "m-maj7") {
          this.setFretLabels(1);
          this.setMarkers(this.minorBarreMajor7);
        }
      } else if(this.musicalKey == "F#") {

      } else if(this.musicalKey == "G") {

      } else if(this.musicalKey == "G#") {

      } else if(this.musicalKey == "A") {

      } else if(this.musicalKey == "A#") {

      } else if(this.musicalKey == "B") {

      } else if(this.musicalKey == "C") {

      } else if(this.musicalKey == "C#") {

      } else if(this.musicalKey == "D") {

      } else if(this.musicalKey == "D#") {

      }
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
.circle {
  width: 5px;
  height: 100px;
  background: black;
  border-radius: 50%;
}
.cross {

}
</style>
