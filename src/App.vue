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

    <ChordDisplay :chord-array="chordArray"
                  :chord-array-index="chordArrayIndex"
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

const openAMajor = {
  firstString:  [0, 0, 0, 0, 0, 0],
  secondString: [0, 1, 0, 0, 0, 0],
  thirdString:  [0, 1, 0, 0, 0, 0],
  fourthString: [0, 1, 0, 0, 0, 0],
  fifthString:  [0, 0, 0, 0, 0, 0],
  sixthString:  [0, 0, 0, 0, 0, 0]
};
const openAMinor = {
  firstString:  [0, 0, 0, 0, 0, 0],
  secondString: [1, 0, 0, 0, 0, 0],
  thirdString:  [0, 1, 0, 0, 0, 0],
  fourthString: [0, 1, 0, 0, 0, 0],
  fifthString:  [0, 0, 0, 0, 0, 0],
  sixthString:  [0, 0, 0, 0, 0, 0]
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
  sixthString:  [1, 0, 0, 0, 0, 0]
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
  sixthString:  [1, 0, 0, 0, 0, 0]
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
      chordArrayIndex: 0
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
    }
  },
  watch: {
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
