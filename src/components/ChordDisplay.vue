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
      <!-- TODO: dynamically change string name based on configuration -->
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
      // variations: root E, root A, ...
      variation: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
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
      firstString: [
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
      major: {
        // major: [ {variation1}, {variation2}, ... ]
        firstString: [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString: [0, 1, 0, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString: [0, 0, 1, 0, 0, 0],
        sixthString: [1, 0, 0, 0, 0, 0]
      },
      minor: {
        firstString: [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString: [1, 0, 0, 0, 0, 0],
        fourthString: [0, 0, 1, 0, 0, 0],
        fifthString: [0, 0, 1, 0, 0, 0],
        sixthString: [1, 0, 0, 0, 0, 0]
      },
      seventh: {
        firstString: [1, 0, 0, 0, 0, 0],
        secondString: [1, 0, 0, 0, 0, 0],
        thirdString: [0, 1, 0, 0, 0, 0],
        fourthString: [1, 0, 0, 0, 0, 0],
        fifthString: [0, 0, 1, 0, 0, 0],
        sixthString: [1, 0, 0, 0, 0, 0]
      }
    }
  },
  mounted() {
    this.$root.$on('send-chord-to-display', chordKeyObject => {
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
      } else if(chordKeyObject.chordType == "7th") {
        for(let i = 0; i < this.firstString.length; i++) {
          this.firstString[i].marker = this.seventh.firstString[i];
          this.secondString[i].marker = this.seventh.secondString[i];
          this.thirdString[i].marker = this.seventh.thirdString[i];
          this.fourthString[i].marker = this.seventh.fourthString[i];
          this.fifthString[i].marker = this.seventh.fifthString[i];
          this.sixthString[i].marker = this.seventh.sixthString[i];
        }
      }
      // TODO: frets based on variations
      let startingFret;
      switch(chordKeyObject.musicalKey) {
          case "E":
            startingFret = -1;
            break;
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
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.chord-display {
  display: flex;
  flex-direction: column;
  padding-left: 5px;
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
.circle {
  width: 5px;
  height: 100px;
  background: gray;
  border-radius: 50%;
  opacity: 45;
}
.cross {
}
.fret {
  flex: 1;
  padding: 0 10px;
  display: flex;
  justify-content: space-between;
  position: relative;
}
.fret:before {
  content: '';
  position: absolute;
  top: 50%;
  left: 0;
  border-top: 1px solid black;
  background: black;
  width: 100%;
  transform: translateY(-50%);
}
.fret:after {
  content: '';
  position: absolute;
  left: 99%;
  top: 0;
  border-right: 1px solid black;
  background: black;
  height: 100%;
}
</style>
