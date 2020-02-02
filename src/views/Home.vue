<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/img01.png"> -->
    <!-- TODO: カウントダウンタイマーの位置をbootで決める。 -->
    <countdownTimer/>
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
