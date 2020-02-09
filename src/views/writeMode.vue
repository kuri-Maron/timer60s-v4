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
              placeholder="Enter something..."
              rows="3"
              max-rows="5"
            ></b-form-textarea>
            <pre class="mt-3 mb-0">{{ text }}</pre>
          </div>
        </div>
      </div>
      <div class="col-3 sideArea">
        <!-- <p>ピンクのサイドバー</p> -->
        <b-button class="rounded-circle minitimer" variant="outline-warning">
          <vac :left-time="60000" :auto-start="false">
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
      text: ""
    };
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
}
</style>