<template>
  <div>
    <countdown :left-time="60000" :auto-start="false" ref="cnt">
      <template v-slot:before>
        <!-- boforeの段階から変数とれんのか？ -->
        <div class="timerNumber">60</div>
        </template>
      <template v-slot:process="anyYouWantedScopName">
        <div class="timerNumber">{{ `${anyYouWantedScopName.timeObj.ceil.s}` }}</div>
      </template>
      <template v-slot:finish>
        <!-- <div>Done!</div> -->
        <div class="timerNumber">END</div>
      </template>
  <b-button class="rounded-circle" variant="success" @click="startTimer">start</b-button>
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
            this.$refs.cnt.startCountdown(true);
        }
    }

};
</script>

<style scoped>

.timerNumber {
    /* font-size: 35vmin; */
    /* font-size: 30vh; */
    font-size: 30vw;
    width: 100%;
    min-height: 100%;
    /* vertical-align: middle; */
    /* TODO: fluxを使い調整してみる or viewport（vh.vm）みたいに親要素の大きさに合わせサイズ指定できる方法は？ */
}

</style>
