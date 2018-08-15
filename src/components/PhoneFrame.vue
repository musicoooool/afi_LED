<template>
  <div class="iphone">
    <img src="../assets/img/iphone.png" alt="iphone">
    <div class="screen">
      <iframe :src="src" frameborder="0" scrolling="no"></iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: "PhoneFrame",
  props: {
    src: String,
    default: "https://www.cbpc.ltd/public/topic/201809/?_simulate=1"
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
/* iphone背景框 */
.iphone {
  margin-top: 10px;
  position: relative;

  img {
    width: 400px;
  }

  .screen {
    position: absolute;
    left: 47px;
    top: 123px;
    border-bottom-right-radius: 15px;
    border-bottom-left-radius: 15px;
    overflow: hidden;
  }

  iframe {
    width: 305px;
    height: 523px;
  }
}
</style>
