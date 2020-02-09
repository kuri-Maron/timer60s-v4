<template>
  <div>
    <countdown :left-time="60000" :auto-start="false" ref="cnt">
      <!-- <countdown :end-time="new Date().getTime() + 60000" :auto-start="false" ref="cnt"> -->
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
      <div class="object">
        <!-- <b-button v-show="!runTimer" class="rounded-circle" variant="outline-success" @click="startTimer"> -->
          <!-- TODO: アイコンホバー時に、カラー変えるか、ハイライトさせたりする。 -->
        <b-icon v-show="!runTimer" icon="play" font-scale="3" class="rounded-circle" variant="success" @click="startTimer">
          start
        </b-icon>
        <!-- <b-button v-show="runTimer" class="rounded-circle" variant="warning" @click="stopTimer">stop</b-button> -->
        <b-icon v-show="runTimer" icon="pause" font-scale="3" class="rounded-circle" variant="warning" @click="stopTimer"></b-icon>
        <!-- <b-button class="rounded-circle" variant="danger" @click="switchTimer">anythig</b-button> -->
      </div>
      <div class="object">
        <b-icon
          icon="arrow-counterclockwise"
          class="rounded-circle p-1"
          variant="dark"
          font-scale="2.5"
          @click="resetTimer"
        ></b-icon>
      </div>
    </countdown>
  </div>
</template>

<script>
import Vue from "vue";
import vueAwesomeCountdown from "vue-awesome-countdown";

Vue.use(vueAwesomeCountdown, "vac"); // Component name, `countdown` and `vac` by default
export default {
  name: "countdownTimer",
  data() {
    return { runTimer: false };
  },
  methods: {
    startTimer() {
      this.$refs.cnt.startCountdown();
      this.runTimer = true;
    },
    stopTimer() {
      // this.$refs.cnt.stopCountdown(); //内部時間が止まらない。
      this.$refs.cnt.pauseCountdown();
      this.runTimer = false;
    },
    resetTimer() {
      this.$refs.cnt.startCountdown(true);
      this.$refs.cnt.pauseCountdown();

      this.runTimer = false;
      // this.$refs.cnt.autoStart="false"
    }
    // 試行メソッド
    // switchTimer() {
    //   this.$refs.cnt.finishCountdown();
    // }
  }
};
</script>

<style scoped>
.timerNumber {
  /* font-size: 35vmin; */
  /* font-size: 30vh; */
  font-size: 25vh;
  width: 100%;
  min-height: 50%;
  margin-top: 17vh;
  display: flex;
  justify-content: center;
  align-items: center;
  /* vertical-align: middle; */
  /* TODO: fluxを使い調整してみる or viewport（vh.vm）みたいに親要素の大きさに合わせサイズ指定できる方法は？ */
}

.object {
  margin: 1vh;
}
</style>
