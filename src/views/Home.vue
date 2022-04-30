<template>
  <div class="app-container">
    <h1>Sailing Right of Way</h1>

    <div class="ocean-container">

      <!--  wind arrow -->
      <windArrow :style="`transform: rotate(${windDirection}deg)`"/>
      
      <!-- boat one blue -->
      <sailBoat
        id="boat-one"
        :style="`transform: rotate(${boatOne.course}deg) translate(${boatOne.xPos}px, ${boatOne.yPos}px)`"
        :sailAngle="boatOne.sailAngle"
      />
      <!-- boat two red -->
      <sailBoat
        id="boat-two"
        :style="`transform: rotate(${boatTwo.course}deg) translate(${boatTwo.xPos}px, ${boatTwo.yPos}px)`"
        :sailAngle="boatTwo.sailAngle"
      />
      
    </div>

    <button
      @click="getNewSituation()"
      style="margin: 10px; padding: 10px;"
    >
    Change Situation
    </button>

  </div>
</template>

<script>
import sailBoat from '../components/sailboat.vue'
import windArrow from '../components/wind-arrow.vue'


function randNum(min, max) {
  return Math.floor(Math.random() * (max - min + 1) + min)
};

export default {
  name: 'Home',
  components: {
    sailBoat, windArrow
  },
  data() {
    return {
      windDirection: 180,
      boatOne: {
        course: 0,
        xPos: 0,
        yPos: 0,
        sailAngle: 0,
      },
      boatTwo: {
        course: 0,
        xPos: 0,
        yPos: 0,
        sailAngle: 0,
      },
    }
  },
  methods: {
    getNewSituation() {
      this.changeWindDirection()
      this.changeBoatParams()
    },
    changeWindDirection() {
      // this.windDirection = randNum(0,360);
    },
    changeBoatParams() {
      let boats = [this.boatOne, this.boatTwo]
      boats.forEach(boat => {
        boat.course = randNum(0,360);
        boat.xPos = randNum(0,175);
        boat.yPos = randNum(0,175);
      });
      console.log('wind direction: ', this.windDirection)
      console.log('blue boat course: ', this.boatOne.course)
      console.log('blue boat position: ', this.boatOne.xPos, this.boatOne.yPos)
      console.log('red boat course: ', this.boatTwo.course)
      console.log('red boat position: ', this.boatTwo.xPos, this.boatTwo.yPos)
    }
  }
}
</script>

<style scoped>

.app-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  margin: 30px;
}

.ocean-container {
  border: 3px solid rgb(29, 29, 164);
  border-radius: 15px;
  width: 500px;
  height: 500px;
  position: relative;
  display: flex;
  justify-content: space-around;
  overflow: hidden;
}

#boat-one {
  fill: blue;
}

#boat-two {
  fill: red;
}

</style>
