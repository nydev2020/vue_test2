<template>
  <div class="main">
    <button v-on:click="myAnimation = 'slide'">Slide</button>
    <button v-on:click="myAnimation = 'fade'">Fade</button>
    <p>{{ myAnimation }}</p>
    <button v-on:click="show = !show">切替</button>
    <transition name="fade" mode="out-in">
      <p v-if="show" key="bye">さよなら</p>
      <p v-else key="hello">こんにちは</p>
    </transition>
    <transition name="fade" enter-active-class="animated bounce">
      <p v-if="show">Hello</p>
    </transition>
    <transition v-bind:name="myAnimation" appear>
      <p v-if="show">slide</p>
    </transition>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      show: true,
      myAnimation: "slide"
    };
  }
};
</script>

<style scoped>
.main {
  padding: 200px;
  width: 100%;
  margin: 0 auto;
}
.fade-enter {
  opacity: 0;
}
.fade-enter-active {
  transition: opacity .5s;
}
.fade-enter-to {
  opacity: 1;
}
.fade-leave {
  opacity: 1;
}
.fade-leave-active {
  transition: opacity .5s;
}
.fade-leave-to {
  opacity: 0;
}

.slide-enter,
.slide-leave-to {
  opacity: 0;
}
.slide-enter-active {
  animation: slide-in 0.5s;
  transition: .5s;
}
.slide-leave-active {
  animation: slide-in 0.5s reverse;
  transition: .5s;
}
@keyframes slide-in {
  from {
    transform: translateX(100px)
  }
  to {
    transform: translateX(0)
  }
}

</style>