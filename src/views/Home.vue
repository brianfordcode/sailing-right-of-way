<template>
  <div class="app-container">
    <h1>Sailing Right of Way</h1>

    <div class="ocean-container">

      <windArrow
        :style="`transform: rotate(${windDirection}deg)`"
      />
      
      <!-- boat one blue -->
      <sailBoat
        id="boat-one"
        :style="`transform: rotate(${boatOne.course}deg) translate(${boatOne.xPos}px, ${boatOne.yPos}px)`"
      />
      <!-- boat two red -->
      <sailBoat
        id="boat-two"
        :style="`transform: rotate(${boatTwo.course}deg) translate(${boatTwo.xPos}px, ${boatTwo.yPos}px)`"
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
        // 360DEG COMPASS
        course: 200,
        // BETWEEN -200 AN 200
        xPos: 0,
        yPos: 0,
      },
      boatTwo: {
        // 360DEG COMPASS
        course: 200,
        // BETWEEN -200 AN 200
        xPos: 0,
        yPos: 0,
      },
    }
  },
  methods: {
    getNewSituation() {
      this.changeWindDirection()
      this.changeBoatParams()
    },
    changeWindDirection() {
      this.windDirection = randNum(0,360);
    },
    changeBoatParams() {
      let boats = [this.boatOne, this.boatTwo]
      boats.forEach(boat => {
        boat.course = randNum(0,360);
        boat.xPos = randNum(0,200);
        boat.yPos = randNum(0,200);
      });

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
