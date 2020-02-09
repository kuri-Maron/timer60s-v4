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
              max-rows="6"
            ></b-form-textarea>

            <pre class="mt-3 mb-0">{{ text }}</pre>
          </div>
        </div>
      </div>
      <div class="col-3 sideArea">ピンクのサイドバー</div>
    </div>
  </div>
  <!-- </div> -->
</template>

<script>
export default {
  name: "writeMode",
   data() {
      return {
        text: ''
      }
    }
  // components: {}
};
</script>

<style scoped>
div {
  border: 1px solid;
}

.sideArea {
  min-height: 70vh;
  max-height: 75vh;
}
</style>