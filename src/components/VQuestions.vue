<template>
  <div class="center">
    <h2>{{curQuestion.title}}</h2>
    <ul>
      <li v-for="(item,i) in curQuestion.option" :key="i+'_'+idx">{{['A','B','C','D','E','F','G'][i]}}、{{item}}</li>
    </ul>
    <div class="prize_code">【{{nums}}】</div>
    <transition name="fade">
      <p v-show="showResult">正确答案: {{curAnswer}}</p>
    </transition>
    <div class="actions">
      <button @click="showAnswer">查看答案</button>
      <button @click="refreshQuestion">{{qToggle?'暂停':'下一题'}}</button>
    </div>
    <audio src="/audio/bgm.mp3" ref="audio"></audio>
  </div>
</template>
<script>
import questions from "../assets/question.js";

export default {
  data() {
    return {
      intervalId: "",
      idx: Math.floor(Math.random() * questions.length),
      showResult: false,
      qToggle: false,
      audio: "",
      nums: ""
    };
  },
  computed: {
    curQuestion() {
      return questions[this.idx];
    },
    curAnswer() {
      let { answer } = this.curQuestion;
      if (typeof answer === "number") {
        answer = [answer];
      }
      return answer
        .map(item => ["A", "B", "C", "D", "E", "F", "G"][item])
        .join("、");
    }
  },
  methods: {
    prepareQuestion() {
      this.idx = Math.floor(Math.random() * questions.length);
      this.nums = Math.ceil(Math.random() * 90);
    },
    showAnswer() {
      this.showResult = true;
    },
    refreshQuestion() {
      this.qToggle = !this.qToggle;
      if (!this.qToggle) {
        clearInterval(this.intervalId);
        this.audio.pause();
        this.audio.currentTime = 0;
        return;
      }
      this.showResult = false;
      this.intervalId = setInterval(() => {
        this.prepareQuestion();
      }, 50);
      this.playMusic();
    },
    playMusic() {
      this.audio.play();
    }
  },
  mounted() {
    this.prepareQuestion();
    this.audio = this.$refs.audio;
  }
};
</script>

<style lang="less" scoped>
.center {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-height: 800px;
  height: 400px;
  padding: 40px 80px;
  h2 {
    font-size: 45pt;
    font-weight: normal;
    margin: 0;
  }
  ul {
    font-size: 35pt;
    list-style: none;
    margin: 0.5em 0;
    li {
      padding: 10px 0;
    }
  }
  p {
    font-size: 35pt;
    margin: 0;
    border: 1px solid #fff;
    padding: 15px;
  }
  button {
    display: inline-block;
    line-height: 1;
    white-space: nowrap;
    cursor: pointer;
    background: #fff;
    border: 1px solid #dcdfe6;
    border-color: #dcdfe6;
    color: #606266;
    -webkit-appearance: none;
    text-align: center;
    box-sizing: border-box;
    outline: none;
    margin: 0;
    transition: 0.1s;
    font-weight: 500;
    user-select: none;
    padding: 12px 20px;
    font-size: 14px;
    border-radius: 4px;
  }
  button {
    &:last-child {
      margin-left: 20px;
      color: #fff;
      background-color: #409eff;
      border-color: #409eff;
    }
  }
  .actions {
    position: absolute;
    bottom: 30px;
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.prize_code {
  font-size: 50pt;
}
</style>
