<template>
  <div class="container">
    <div v-if="showTime">
      <img alt="tired" src="../assets/sad.jpg">
      <h1 id="timer"></h1>
      <h3>Almost...</h3>
    </div>
    <div v-else >
      <img alt="later" src="../assets/later.jpg">
      <h3 class="pt-5">Later Bitchachoes!</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Timer',
  data() {
    return {
      showTime: true
    }
  },
  mounted() {
    let now = new Date();
    if (now.getHours() >= 17 ) { 
      this.showTime = false
    } else {
      this.startTimer(now);
    }
  },
  methods: {
    startTimer(timeNow) {
      let _this = this
      let now = timeNow
      let fivePm = now.setHours(17,0,0,0);
      var interval = setInterval(function() {
        let elapsedTime = fivePm - Date.now();

        if (elapsedTime <= 0) {
          _this.letsGo()
          clearInterval(interval);
        }

        let hours = Math.floor(elapsedTime / 3600000);
        let minsInMs = Math.floor(elapsedTime % 3600000);
        if (document.getElementById("timer")) {
          document.getElementById("timer").innerHTML = `${hours}.${minsInMs}`
        }
      }, 1);
    },
    letsGo() {
      this.showTime = false
    }
  }
}
</script>

<style scoped lang="scss">
h1 {
  padding-top: 3rem;
  font-size: 6vw;
}
h1::before {
  content: "Hr";
  font-size: 2.5vw;
  color: red;
  display: inline-block;
  -webkit-transform: rotate(-90deg);
  -moz-transform: rotate(-90deg);
  -o-transform: rotate(-90deg);
  -ms-transform: rotate(-90deg);
  transform: rotate(-90deg);
}

img {
  width: 100%;
  max-width: 350px;
  height: auto;
  border-radius: 10px;
}
</style>
