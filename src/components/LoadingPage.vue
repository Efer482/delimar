<template>
  <transition name="fade">
    <div class="body vh-100 splash" v-show="!isloader">
      <div class="logo_nombre">
        <h1>DeliMar</h1>
      </div>
    </div>
  </transition>
</template>
<script>
export default {
  name: "LoadingPage",
  props: {
    msg: String,
  },
  data() {
    return {
      isloader: false,
    };
  },
  mounted() {
    document.onreadystatechange = () => {
      if (document.readyState == "complete") {
        this.isloader = true;
      }
    };
  },
};
</script>

<style scoped>
* {
  padding: 0;
  margin: 0;
}
.splash > .logo_nombre img {
  width: 100%;
  margin: 4%;
}
.splash > .logo_nombre h1 {
  font-size: 15vw;
}
.splash {
  display: flex;
  position: fixed;
  justify-content: center;
  align-items: center;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: 999;
  background-image: url(../img/min/background.png);
  background-position: 65%;
  background-attachment: fixed;
  background-size: cover;
  background-repeat: no-repeat;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
