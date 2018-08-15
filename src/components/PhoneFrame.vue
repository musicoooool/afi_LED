<template>
  <div class="iphone margin-bottom-0">
    <img src="../assets/img/iphone.png" alt="iphone">
    <div class="screen">
      <iframe name="_phoneFrame" :src="src" frameborder="0" scrolling="no"></iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: "PhoneFrame",
  props: {
    src: {
      type: String,
      default: "https://www.cbpc.ltd/public/topic/201809/?_simulate=1"
    },
    autoLoad: {
      type: int,
      default: 0
    }
  },
  data() {
    return {
      itv: ""
    };
  },
  mounted() {
    if (this.autoLoad > 0) {
      this.itv = setInterval(() => {
        // document.all._phoneFrame.contentWindow.location.reload(true);
        document.all._phoneFrame.src = this.src;
      }, autoLoad * 1000);
    }
  },
  beforeDestroy() {
    if (this.autoLoad > 0) {
      clearInterval(this.itv);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
/* iphone背景框 */
.iphone {
  margin: 10px;
  position: relative;

  img {
    width: 349px;
  }

  .screen {
    position: absolute;
    left: 22px;
    top: 117px;
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
