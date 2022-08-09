<template >
  <div class="container">
    <div class="text-box">
      <div class="screen-box">
        <h2 class="text-white">At first, there was nothing...</h2>
      </div>

      <div class="screen-box">
        <h2 class="text-white">But then..</h2>
      </div>

      <div class="screen-box">
        <h2 class="text-white">We came and changed everything</h2>
      </div>

      <div class="screen-box">
        <h2 class="text-black">Company name. Changing the world.</h2>
      </div>
    </div>
    <div class="video-box">
      <video muted preload>
        <source src="/video/2.mov" />
        <p>Your user agent does not support the HTML5 Video element.</p>
      </video>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      video: "",
      duration: "",
      currentTime: "",
      currentScroll: "",
      maxScroll: "",
      constant: "",
    };
  },
  mounted() {
    document.addEventListener("scroll", this.handleScroll, false);
    this.video = document.querySelector("video");
    this.maxScroll = document.body.offsetHeight - window.innerHeight;
  },
  methods: {
    handleScroll() {
      if (!this.duration) {
        this.duration = this.video.duration;
      }

      if (!this.constant) {
        this.constant = this.maxScroll / this.duration;
      }

      this.currentScroll = window.scrollY;
      this.currentTime = this.currentScroll / this.constant;
      this.video.currentTime = this.currentTime;
    },
  },
  unmounted() {
    document.removeEventListener("scroll", this.handleScroll, false);
  },
};
</script>

<style>
#app {
  font-family: "Montserrat", sans-serif;
  font-weight: 600;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
}

.text-box {
  z-index: 1;
}

.text-white {
  color: white;
}

.text-black {
  color: black;
}

.container {
  display: grid;
  /* grid-template-columns: repeat(2, 1fr); */
}

.screen-box {
  display: flex;
  height: 100vh;
  align-items: center;
  justify-content: center;
}

h2 {
  font-size: 3rem;
  text-align: center;
}

video {
  width: 100%;
  height: 100vh;
  position: fixed;
  top: 0;
  right: 0;
  object-fit: cover;
}
</style>
