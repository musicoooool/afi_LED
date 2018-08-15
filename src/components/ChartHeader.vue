<template>
  <div class="col-1">
    <div class="title">某活动应用运行情况</div>
    <div class="subtitle">{{now}}</div>
  </div>
</template>
<script>
import dayjs from "dayjs";
export default {
  data() {
    return {
      now: "",
      itv: ""
    };
  },
  mounted() {
    this.itv = setInterval(() => {
      this.now = dayjs().format("YYYY-MM-DD HH:mm:ss");
    }, 1000);
  },
  beforeDestroy() {
    clearInterval(this.itv);
  }
};
</script>

<style lang="less" scoped>
.title {
  font-size: 3rem;
  font-weight: lighter;
  text-align: center;
  margin-top: 10px;
}
.subtitle {
  text-align: center;
}
</style>