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
      <!-- <sailBoat id="boat-two"/> -->
      
    </div>

    <button
      @click="changeWindDirection"
      style="margin: 10px; padding: 10px;"
    >
    Change Wind
    </button>

  </div>
</template>

<script>
import sailBoat from '../components/sailboat.vue'
import windArrow from '../components/wind-arrow.vue'


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
        course: 0,
        // BETWEEN -200 AN 200
        xPos: 0,
        yPos: 0,
      },
    }
  },
  methods: {
    changeWindDirection() {
      this.windDirection = Math.floor(Math.random() * (360 - 0 + 1) + 0)
      console.log(this.windDirection)
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
