<template>
  <div class="app-container">
    <h1>Sailing Right of Way</h1>

    <div class="ocean-container">

      <!--  wind arrow -->
      <windArrow :style="`transform: rotate(${windDirection}deg)`"/>
      
      <!-- boat one blue -->
      <sailBoat
        v-for="boat in boats"
        :key="boat"
        :style="`transform: rotate(${boat.course}deg) translate(${boat.xPos}px, ${boat.yPos}px); fill: ${boat.color}`"
        :sailAngle="boat.sailAngle"
        :course="boat.course"
      />
      
    </div>

    <p>{{boats[0].sailAngle}}</p>
    <p>{{boats[1].sailAngle}}</p>

    <!-- new situation -->
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
      boats: [
        {
          type: 'sail',
          color: 'blue',
          course: 0,
          xPos: 0,
          yPos: 0,
          pointOfSail: '',
          sailAngle: 0,
        },
        {
          type: 'sail',
          color: 'red',
          course: 0,
          xPos: 0,
          yPos: 0,
          pointOfSail: '',
          sailAngle: 0,
        }
      ],
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
      this.boats.forEach(boat => {
        boat.course = randNum(35,325);
        boat.xPos = randNum(0,175);
        boat.yPos = randNum(0,175);
        boat.sailAngle = -boat.course/2

        // points of sail
        const portCloseHaul = boat.course > 0 && boat.course < 45;
        const portBeamReach = boat.course > 45 && boat.course < 135;
        const portBroadReach = boat.course > 135 && boat.course < 180;
        const starboardBroadReach = boat.course > 180 || boat.course < 225;
        const starboardBeamReach = boat.course > 225 || boat.course < 315;
        const starboardCloseHaul = boat.course > 315 || boat.course < 360;

        console.log(boat.color, boat.course)

        if (boat.course > 180) { boat.sailAngle = boat.sailAngle - 180 }

        // if (boat.course < )







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

</style>
