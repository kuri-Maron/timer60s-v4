<template>
  <div>
    <!-- <h1>スマホ、PCで書きながら時間測定。</h1> -->
    <!-- <div class="container"> -->
    <div class="row">
      <div class="col-9">
        <div class="row">
          <div class="col">
            <b-form-textarea
              id="textarea"
              v-model="text"
              placeholder="think..."
              rows="3"
              max-rows="5"
            ></b-form-textarea>
            <pre class="mt-5 mb-0">{{ text }}</pre>
          </div>
        </div>
      </div>
      <div class="col-3 sideArea">
          <!-- TODO: ボタンをもう少しボタンぽくする -->
        <b-button class="rounded-circle minitimer" :variant="variantColer" @click="doTimer">
          <vac :left-time="60000" :auto-start="false" ref="cnt">
            <template v-slot:before>
              <!-- boforeの段階から変数とれんのか？ -->
              <span>60</span>
            </template>
            <template v-slot:process="{ timeObj }">
              <span>{{timeObj.s}}</span>
            </template>
            <template v-slot:finish>
              <span>Done!</span>
            </template>
          </vac>
        </b-button>
        <!-- TODO: 垂直にリセットボタンなど追加 -->
      </div>
    </div>
  </div>
  <!-- </div> -->
</template>

<script>
import Vue from "vue";
import vueAwesomeCountdown from "vue-awesome-countdown";

Vue.use(vueAwesomeCountdown, "vac");

export default {
  name: "writeMode",
  data() {
    return {
      text: "",
      runTimer: false,
      variantColer: "outline-warning"
    };
  },
  methods: {
      doTimer() {
          if(this.runTimer){
              this.stopTimer();
          }else {
              this.startTimer();
          }
      },
      startTimer() {
      this.$refs.cnt.startCountdown();
      this.runTimer = true;
      this.variantColer = "outline-success"
    },
    stopTimer() {
        // this.$refs.cnt.stopCountdown(); //内部時間が止まらない。
      this.$refs.cnt.pauseCountdown();
      this.runTimer = false;
      this.variantColer = "outline-warning"
    },
    // TODO: リセットメソッド実装
  }
  // components: {}
};
</script>

<style scoped>
div {
  /* border: 1px solid; */
}

pre {
  color: azure;
  border :1px solid #42b983;
  min-height: 55vh;
  padding: 2em;
}

.sideArea {
  min-height: 70vh;
  max-height: 75vh;
}

.minitimer {
  font-size: 10vmin;
}

#textarea {
    background-color: #444;
    color: azure;
    border :1px solid #42b983;
    margin-top: 4vh;
}
</style>