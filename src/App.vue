<template>
  <div id="app">
    <Picker @send-musical-key-to-root="updateMusicalKey"
            @send-chord-type-to-root="updateChordType"
            @decrease-chord-array-index="updateChordArrayIndex"
            @increase-chord-array-index="updateChordArrayIndex"
            :musical-key="musicalKey"
            :chord-type="chordType"
            :chord-array="chordArray"
            :chord-array-index="chordArrayIndex"
    >
    </Picker>

    <ChordDisplay
                  :chord-array="chordArray"
                  :chord-array-index="chordArrayIndex"
                  :fret-labels="fretLabels"
                  :first-string="firstString"
                  :second-string="secondString"
                  :third-string="thirdString"
                  :fourth-string="fourthString"
                  :fifth-string="fifthString"
                  :sixth-string="sixthString"
    >
    </ChordDisplay>
  </div>
</template>

<script>
import Picker from './components/Picker.vue';
import ChordDisplay from './components/ChordDisplay.vue';

/*
const blank = {
  firstString:  [0, 0, 0, 0, 0, 0],
  secondString: [0, 0, 0, 0, 0, 0],
  thirdString:  [0, 0, 0, 0, 0, 0],
  fourthString: [0, 0, 0, 0, 0, 0],
  fifthString:  [0, 0, 0, 0, 0, 0],
  sixthString:  [0, 0, 0, 0, 0, 0]
};
*/
const openCMajor = {
  firstString:  [0, 0, 0, 0, 0, 0],
  secondString: [1, 0, 0, 0, 0, 0],
  thirdString:  [0, 0, 0, 0, 0, 0],
  fourthString: [0, 1, 0, 0, 0, 0],
  fifthString:  [0, 0, 1, 0, 0, 0],
  sixthString:  [2, 0, 0, 0, 0, 0]
};
const openAMajor = {
  firstString:  [0, 0, 0, 0, 0, 0],
  secondString: [0, 1, 0, 0, 0, 0],
  thirdString:  [0, 1, 0, 0, 0, 0],
  fourthString: [0, 1, 0, 0, 0, 0],
  fifthString:  [0, 0, 0, 0, 0, 0],
  sixthString:  [2, 0, 0, 0, 0, 0]
};
const openAMinor = {
  firstString:  [0, 0, 0, 0, 0, 0],
  secondString: [1, 0, 0, 0, 0, 0],
  thirdString:  [0, 1, 0, 0, 0, 0],
  fourthString: [0, 1, 0, 0, 0, 0],
  fifthString:  [0, 0, 0, 0, 0, 0],
  sixthString:  [2, 0, 0, 0, 0, 0]
};
const openGMajor = {
  firstString:  [0, 0, 1, 0, 0, 0],
  secondString: [0, 0, 0, 0, 0, 0],
  thirdString:  [0, 0, 0, 0, 0, 0],
  fourthString: [0, 0, 0, 0, 0, 0],
  fifthString:  [0, 1, 0, 0, 0, 0],
  sixthString:  [0, 0, 1, 0, 0, 0]
};
const openEMajor = {
  firstString:  [0, 0, 0, 0, 0, 0],
  secondString: [0, 0, 0, 0, 0, 0],
  thirdString:  [1, 0, 0, 0, 0, 0],
  fourthString: [0, 1, 0, 0, 0, 0],
  fifthString:  [0, 1, 0, 0, 0, 0],
  sixthString:  [0, 0, 0, 0, 0, 0]
};
const openEMinor = {
  firstString:  [0, 0, 0, 0, 0, 0],
  secondString: [0, 0, 0, 0, 0, 0],
  thirdString:  [0, 0, 0, 0, 0, 0],
  fourthString: [0, 1, 0, 0, 0, 0],
  fifthString:  [0, 1, 0, 0, 0, 0],
  sixthString:  [0, 0, 0, 0, 0, 0]
};
const openDMajor = {
  firstString:  [0, 1, 0, 0, 0, 0],
  secondString: [0, 0, 1, 0, 0, 0],
  thirdString:  [0, 1, 0, 0, 0, 0],
  fourthString: [0, 0, 0, 0, 0, 0],
  fifthString:  [2, 0, 0, 0, 0, 0],
  sixthString:  [2, 0, 0, 0, 0, 0]
};
const openDMinor = {
  firstString:  [1, 0, 0, 0, 0, 0],
  secondString: [0, 0, 1, 0, 0, 0],
  thirdString:  [0, 1, 0, 0, 0, 0],
  fourthString: [0, 0, 0, 0, 0, 0],
  fifthString:  [2, 0, 0, 0, 0, 0],
  sixthString:  [2, 0, 0, 0, 0, 0]
};
const barreMajor1 = {
  firstString:  [1, 0, 0, 0, 0, 0],
  secondString: [1, 0, 0, 0, 0, 0],
  thirdString:  [0, 1, 0, 0, 0, 0],
  fourthString: [0, 0, 1, 0, 0, 0],
  fifthString:  [0, 0, 1, 0, 0, 0],
  sixthString:  [1, 0, 0, 0, 0, 0]
};
const barreMajor2 = {
  firstString:  [1, 0, 0, 0, 0, 0],
  secondString: [0, 0, 1, 0, 0, 0],
  thirdString:  [0, 0, 1, 0, 0, 0],
  fourthString: [0, 0, 1, 0, 0, 0],
  fifthString:  [1, 0, 0, 0, 0, 0],
  sixthString:  [2, 0, 0, 0, 0, 0]
};
const barreMinor1 = {
  firstString:  [1, 0, 0, 0, 0, 0],
  secondString: [1, 0, 0, 0, 0, 0],
  thirdString:  [1, 0, 0, 0, 0, 0],
  fourthString: [0, 0, 1, 0, 0, 0],
  fifthString:  [0, 0, 1, 0, 0, 0],
  sixthString:  [1, 0, 0, 0, 0, 0]
};
const barreMinor2 = {
  firstString:  [1, 0, 0, 0, 0, 0],
  secondString: [0, 1, 0, 0, 0, 0],
  thirdString:  [0, 0, 1, 0, 0, 0],
  fourthString: [0, 0, 1, 0, 0, 0],
  fifthString:  [1, 0, 0, 0, 0, 0],
  sixthString:  [2, 0, 0, 0, 0, 0]
}
//
//
//

const aMajor = [
  {
    startingFret: 1,
    chordPattern: openAMajor
  },
  {
    startingFret: 5,
    chordPattern: barreMajor1
  },
  {
    startingFret: 12,
    chordPattern: barreMajor2
  }
];
const aMinor = [
  {
    startingFret: 1,
    chordPattern: openAMinor
  },
  {
    startingFret: 5,
    chordPattern: barreMinor1
  }
];
const aSharpMajor = [
  {
    startingFret: 1,
    chordPattern: barreMajor2
  },
  {
    startingFret: 6,
    chordPattern: barreMajor1
  }
];
const aSharpMinor = [
  {
    startingFret: 1,
    chordPattern: barreMinor2
  },
  {
    startingFret: 6,
    chordPattern: barreMinor1
  }
];
const bMajor = [
  {
    startingFret: 2,
    chordPattern: barreMajor2
  },
  {
    startingFret: 7,
    chordPattern: barreMajor1
  }
];
const bMinor = [
  {
    startingFret: 2,
    chordPattern: barreMinor2
  },
  {
    startingFret: 7,
    chordPattern: barreMinor1
  }
];
const cMajor = [
  {
    startingFret: 1,
    chordPattern: openCMajor
  },
  {
    startingFret: 3,
    chordPattern: barreMajor2
  },
  {
    startingFret: 8,
    chordPattern: barreMajor1
  }
];
const cMinor = [
  {
    startingFret: 3,
    chordPattern: barreMinor2
  },
  {
    startingFret: 8,
    chordPattern: barreMinor1
  }
];
const cSharpMajor = [
  {
    startingFret: 4,
    chordPattern: barreMajor2
  },
  {
    startingFret: 9,
    chordPattern: barreMajor1
  }
];
const cSharpMinor = [
  {
    startingFret: 4,
    chordPattern: barreMinor2
  },
  {
    startingFret: 9,
    chordPattern: barreMinor1
  }
];
const dMajor = [
  {
    startingFret: 1,
    chordPattern: openDMajor
  },
  {
    startingFret: 5,
    chordPattern: barreMajor2
  },
  {
    startingFret: 10,
    chordPattern: barreMajor1
  }
];
const dMinor = [
  {
    startingFret: 1,
    chordPattern: openDMinor
  },
  {
    startingFret: 5,
    chordPattern: barreMinor2
  },
  {
    startingFret: 10,
    chordPattern: barreMinor1
  }
];
const dSharpMajor = [
  {
    startingFret: 6,
    chordPattern: barreMajor2
  },
  {
    startingFret: 11,
    chordPattern: barreMajor1
  }
];
const dSharpMinor = [
  {
    startingFret: 6,
    chordPattern: barreMinor2
  },
  {
    startingFret: 11,
    chordPattern: barreMinor1
  }
];
const eMajor = [
  {
    startingFret: 1,
    chordPattern: openEMajor
  },
  {
    startingFret: 7,
    chordPattern: barreMajor2
  }
];
const eMinor = [
  {
    startingFret: 1,
    chordPattern: openEMinor
  },
  {
    startingFret: 7,
    chordPattern: barreMinor2
  }
];
const fMajor = [
  {
    startingFret: 1,
    chordPattern: barreMajor1
  },
  {
    startingFret: 8,
    chordPattern: barreMajor2
  }
];
const fMinor = [
  {
    startingFret: 1,
    chordPattern: barreMinor1
  },
  {
    startingFret: 8,
    chordPattern: barreMinor2
  }
];
const fSharpMajor = [
  {
    startingFret: 2,
    chordPattern: barreMajor1
  },
  {
    startingFret: 9,
    chordPattern: barreMajor2
  }
];
const fSharpMinor = [
  {
    startingFret: 2,
    chordPattern: barreMinor1
  },
  {
    startingFret: 9,
    chordPattern: barreMinor2
  }
];
const gMajor = [
  {
    startingFret: 1,
    chordPattern: openGMajor
  },
  {
    startingFret: 3,
    chordPattern: barreMajor1
  },
  {
    startingFret: 10,
    chordPattern: barreMajor2
  }
];
const gMinor = [
  {
    startingFret: 3,
    chordPattern: barreMinor1
  },
  {
    startingFret: 10,
    chordPattern: barreMinor2
  }
];
const gSharpMajor = [
  {
    startingFret: 4,
    chordPattern: barreMajor1
  },
  {
    startingFret: 11,
    chordPattern: barreMajor2
  }
];
const gSharpMinor = [
  {
    startingFret: 4,
    chordPattern: barreMinor1
  },
  {
    startingFret: 11,
    chordPattern: barreMinor2
  }
];


export default {
  name: 'app',
  components: {
    Picker,
    ChordDisplay
  },
  data() {
    return {
      musicalKey: "A",
      chordType: "Major",
      chordArray: aMajor,
      chordArrayIndex: 0,
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
          marker: 2
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
  methods: {
    updateMusicalKey(newMusicalKey) {
      this.musicalKey = newMusicalKey;
    },
    updateChordType(newChordType) {
      this.chordType = newChordType;
    },
    updateChordArrayIndex(newIndex) {
      this.chordArrayIndex = newIndex;
    },
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
    }
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
    musicalKey(newVal, oldVal) {
      this.chordArrayIndex = 0;
      if(newVal == "E") {
        if(this.chordType == "Major") {
          this.chordArray = eMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = eMinor;
        }
      } else if(newVal == "F") {
        if(this.chordType == "Major") {
          this.chordArray = fMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = fMinor;
        }
      } else if(newVal == "F#") {
        if(this.chordType == "Major") {
          this.chordArray = fSharpMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = fSharpMinor;
        }
      } else if(newVal == "G") {
        if(this.chordType == "Major") {
          this.chordArray = gMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = gMinor;
        }
      } else if(newVal == "G#") {
        if(this.chordType == "Major") {
          this.chordArray = gSharpMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = gSharpMinor;
        }
      } else if(newVal == "A") {
        if(this.chordType == "Major") {
          this.chordArray = aMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = aMinor;
        }
      } else if(newVal == "A#") {
        if(this.chordType == "Major") {
          this.chordArray = aSharpMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = aSharpMinor;
        }
      } else if(newVal == "B") {
        if(this.chordType == "Major") {
          this.chordArray = bMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = bMinor;
        }
      } else if(newVal == "C") {
        if(this.chordType == "Major") {
          this.chordArray = cMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = cMinor;
        }
      } else if(newVal == "C#") {
        if(this.chordType == "Major") {
          this.chordArray = cSharpMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = cSharpMinor;
        }
      } else if(newVal == "D") {
        if(this.chordType == "Major") {
          this.chordArray = dMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = dMinor;
        }
      } else {  // D#
        if(this.chordType == "Major") {
          this.chordArray = dSharpMajor;
        } else if(this.chordType == "Minor") {
          this.chordArray = dSharpMinor;
        }
      }
    },
    chordType(newVal, oldVal) {
      this.chordArrayIndex = 0;
      if(this.musicalKey == "E") {
        if(newVal == "Major") {
          this.chordArray = eMajor;
        } else if(newVal == "Minor") {
          this.chordArray = eMinor;
        }
      } else if(this.musicalKey == "F") {
        if(newVal == "Major") {
          this.chordArray = fMajor;
        } else if(newVal == "Minor") {
          this.chordArray = fMinor;
        }
      } else if(this.musicalKey == "F#") {
        if(newVal == "Major") {
          this.chordArray = fSharpMajor;
        } else if(newVal == "Minor") {
          this.chordArray = fSharpMinor;
        }
      } else if(this.musicalKey == "G") {
        if(newVal == "Major") {
          this.chordArray = gMajor;
        } else if(newVal == "Minor") {
          this.chordArray = gMinor;
        }
      } else if(this.musicalKey == "G#") {
        if(newVal == "Major") {
          this.chordArray = gSharpMajor;
        } else if(newVal == "Minor") {
          this.chordArray = gSharpMinor;
        }
      } else if(this.musicalKey == "A") {
        if(newVal == "Major") {
          this.chordArray = aMajor;
        } else if(newVal == "Minor") {
          this.chordArray = aMinor;
        }
      } else if(this.musicalKey == "A#") {
        if(newVal == "Major") {
          this.chordArray = aSharpMajor;
        } else if(newVal == "Minor") {
          this.chordArray = aSharpMinor;
        }
      } else if(this.musicalKey == "B") {
        if(newVal == "Major") {
          this.chordArray = bMajor;
        } else if(newVal == "Minor") {
          this.chordArray = bMinor;
        }
      } else if(this.musicalKey == "C") {
        if(newVal == "Major") {
          this.chordArray = cMajor;
        } else if(newVal == "Minor") {
          this.chordArray = cMinor;
        }
      } else if(this.musicalKey == "C#") {
        if(newVal == "Major") {
          this.chordArray = cSharpMajor;
        } else if(newVal == "Minor") {
          this.chordArray = cSharpMinor;
        }
      } else if(this.musicalKey == "D") {
        if(newVal == "Major") {
          this.chordArray = dMajor;
        } else if(newVal == "Minor") {
          this.chordArray = dMinor;
        }
      } else {  // D#
        if(newVal == "Major") {
          this.chordArray = dSharpMajor;
        } else if(newVal == "Minor") {
          this.chordArray = dSharpMinor;
        }
      }
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
