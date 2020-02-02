<template>
  <div>
    <countdown :left-time="60000" class="timerNumber">
      <template v-slot:process="anyYouWantedScopName">
        <span>{{ `${anyYouWantedScopName.timeObj.ceil.s}` }}</span>
      </template>
      <template v-slot:finish>
        <span>Done!</span>
      </template>
    </countdown>
  </div>
</template>

<script>
import Vue from 'vue'
import vueAwesomeCountdown from 'vue-awesome-countdown'

Vue.use(vueAwesomeCountdown, 'vac') // Component name, `countdown` and `vac` by default
export default {
    name: "countdownTimer",
    methods: {
        startTimer() {
            
        }
    }

};
</script>

<style scoped>

.timerNumber {
    font-size: 35vmin;
}

</style>
