<template>
  <div class="wrapper" ref="wrapperRef">
    <div class="hero">
      <h1>Click the Button Multiple Times to Make Him Happy</h1>
    </div>
    <div class="image_container">
      <img :src="image1" alt="" />
    </div>
    <div class="theButton">
      <button @click="changeImage" id="thisButton">
        Click me!
      </button>
    </div>
    <div class="retryButton" id="retryButton">
      <button @click="retry">Reset</button>
    </div>
    <div class="happy" id="happy">
      <p>Thank you, I'm now happy</p>
      <p>Thank you, I'm now happy</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      click: 0,
      image1: require("./assets/IncrediblyCanny1.jpg"),
      counter: 0,
      imageChange: [
        require("./assets/IncrediblyCanny2.jpg"),
        require("./assets/IncrediblyCanny3.jpg"),
        require("./assets/IncrediblyCanny4.jpg"),
        require("./assets/IncrediblyCanny5.jpg"),
        require("./assets/IncrediblyCanny6.jpg"),
        require("./assets/IncrediblyCanny7.jpg"),
        require("./assets/IncrediblyCanny8.jpg"),
      ],
    };
  },

  methods: {
    changeImage() {
      if (this.click <= 21) {
        this.click++;
        if (this.click % 3 === 0) {
          this.image1 = this.imageChange[this.counter];
          this.counter++;
        }
      } else {
        this.click += 0;
        let happyDiv = document.getElementById("happy");
        let retryButton = document.getElementById("retryButton");
        let theButton = document.getElementById("thisButton");

        retryButton.style.display = "block";
        happyDiv.style.display = "block";
        theButton.setAttribute("disabled", true);
      }
    },

    retry() {
      this.click = 0;
      this.counter = 0;
      this.image1 = require("./assets/IncrediblyCanny1.jpg");
      let happyDiv = document.getElementById("happy");
      let retryButton = document.getElementById("retryButton");
      let theButton = document.getElementById("thisButton");

      retryButton.style.display = "none";
      happyDiv.style.display = "none";
      theButton.removeAttribute("disabled");
    },
  },
};
</script>

<style>
body {
  margin-top: 50px;
  background-color: #f7f7ff;
  text-align: center;
}

.wrapper .hero h1{
  font-family: poppins;
  margin-bottom: 50px;
  font-weight: bolder;
}

.wrapper .theButton{
  margin-top: 10px;
}

.wrapper .retryButton{
  margin-top: 10px;
}

.wrapper .happy p{
  font-family: poppins;
}

button{
  background-color: #6969B3;
  color: #f7f7ff;
  border: none;
  font-family: poppins;
  font-size: 20px;
  width: 150px;
  height: 50px;
  border-radius: 30px;
}

button:hover{
  background-color: #533A7B;
  cursor: pointer;
}

.wrapper .happyDiv {
  font-size: 20px;
}

.wrapper .retryButton {
  display: none;
}

.wrapper .happy {
  display: none;
}
</style>
