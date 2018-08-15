<template>
  <div class="video-container">
    <video autoplay="autoplay" src="http://videooc.tc.qq.com/vcloud1022.tc.qq.com/1022_d58ddd6573174f89b230cece6cad06d5.f0.mp4?vkey=FFF8C3451A8C48464125A54ED76384E58346457C483E1C7C81C9155F3CFB9207ED863CC1221F9AB85C4C0F37FCF0B40E0BDC26A03E635883D4E9E505AB4613118526A2A1494D9268CB4B82EDB164ED05902CC6DCD0E2CCE6&amp;sha=0" muted="true" loop="true" preload="auto"></video>
  </div>
</template>
<style lang="less" scoped>
// 视频背景
.video-container {
  position: absolute;
  z-index: -2;
  &::before {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(12, 32, 90, 0.59);
  }
}
</style>
