<template>
  <div class="sharingan" @click="test">
    <div class="eye circle center"></div>
    <div class="eye-outer circle center"></div>
    <div class="eye-inner circle center"></div>
    <div class="tomoe-1 tomoe circle"></div>
    <div class="tomoe-2 tomoe circle"></div>
    <div class="tomoe-3 tomoe circle"></div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  methods: {
    test() {
      alert("test");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.sharingan {
  width: 60px;
  height: 60px;
  position: relative;
}
.circle {
  border-radius: 50%;
  position: absolute;
}
.center {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
}
.eye-inner {
  width: 12px;
  height: 12px;
  background-color: #0c0404;
}
.eye-outer {
  width: 35px;
  height: 35px;
  border: 2px solid #0c0404;
}
.eye {
  width: 60px;
  height: 60px;
  background-color: #a50909;
  border: 3px solid #000;
}
.tomoe {
  width: 6px;
  height: 6px;
  position: absolute;
  background-color: #000;
}
.tomoe:after {
  content: "";
  position: absolute;

  top: -2px;
  left: 1px;
  width: 2px;
  height: 3px;

  background-color: #000;

  border-top-left-radius: 40%;
  border-top-right-radius: 0%;
  border-bottom-left-radius: 40%;
  transform: rotate(85deg) skewX(30deg) skewY(30deg);
}
.tomoe-1 {
  top: 10px;
  left: 26px;
  z-index: 1;
}
.tomoe-2 {
  top: 35px;
  left: 42px;
  transform: rotate(130deg);
  z-index: 2;
}
.tomoe-3 {
  top: 35px;
  left: 12px;
  transform: rotate(245deg);
  z-index: 3;
}

@keyframes doujutsu {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(-360deg);
  }
}

.sharingan:hover {
  animation: doujutsu 2s infinite linear;
}
</style>
