<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/img01.png"> -->
    <!-- TODO: カウントダウンタイマーの位置をbootで決める。 -->
    <div class="row timerRow">
    <countdownTimer class="col-8 offset-2">
    </countdownTimer>
    <div class="col-2"></div>
    </div>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
// @ is an alias to /src
import countdownTimer from '@/components/countdownTimer.vue'
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    countdownTimer,
    // HelloWorld
  }
}
</script>


<style scoped>
.timerRow {
max-width: 100vw;
height: 35vh;
}
</style>