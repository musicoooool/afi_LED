<template>
  <div id="app">
    <VideoCanvas/>
    <router-view/>
  </div>
</template>
<script>
import VideoCanvas from "@/components/VideoCanvas.vue";
export default {
  components: {
    VideoCanvas
  }
};
</script>

<style lang="less">
@import "./assets/less/layout.less";
body,
html,
#app {
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 0;
  overflow: hidden;
}

#app {
  color: #fff;
}
// .__wrapper {
//   position: absolute;
//   opacity: 0.2;
//   z-index: -1;
// }
</style>
