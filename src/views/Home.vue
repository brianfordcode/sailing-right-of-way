<template>
  <div class="app-container">
    <h1>Sailing Right of Way</h1>

    <div class="ocean-container">

      <windArrow
        :style="`transform: rotate(${windDirection}deg)`"
      />
      
      <!-- boat one blue -->
      <!-- <sailBoat id="boat-one"/> -->
      <!-- boat two red -->
      <!-- <sailBoat id="boat-two"/> -->
      
    </div>
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
}

#boat-one {
  fill: blue;
  transform: translateX(50px);
}

#boat-two {
  fill: red;
  transform: translateX(-50px);
}

</style>
