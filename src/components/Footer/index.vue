<template>
  <footer>
    <div class="power" v-show="!store.playerState">
      <span
        >&nbsp;&copy;&nbsp;{{ fullYear }}
        <a href="https://tianxiaomu.cn">沐澄</a>
      </span>
      &nbsp;&copy;&nbsp;
      <!-- 站点备案 -->
      <a href="https://beian.miit.gov.cn" target="_blank">鄂ICP备2022019515号</a>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      <a href="https://www.upyun.com/?utm_source=lianmeng&utm_medium=referral">本网站由<img style="width: 50px;" src="https://cdn.jsdelivr.net/gh/tianxincc/PicGo@main/Anime/202203282309196.png" alt="logo"/> 提供CDN加速/云存储服务 </a>
    </div>
    <div class="lrc" v-show="store.playerState">
      <music-one theme="filled" size="18" fill="#efefef" />
      <span class="lrc-text">
        {{ store.getPlayerLrc ? store.getPlayerLrc : "这句没有歌词" }}
      </span>
      <music-one theme="filled" size="18" fill="#efefef" />
    </div>
  </footer>
</template>

<script setup>
import { MusicOne } from "@icon-park/vue-next";
import { mainStore } from "@/store";
import config from "@/../package.json";
const store = mainStore();

let fullYear = new Date().getFullYear();
</script>

<style lang="scss" scoped>
footer {
  width: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  height: 46px;
  line-height: 46px;
  text-align: center;
  backdrop-filter: blur(10px);
  background: rgb(0 0 0 / 25%);
  z-index: 0;
  animation: fade;
  -webkit-animation: fade 0.5s;
  @media (max-width: 720px) {
    font-size: 0.85rem;
  }
  @media (max-width: 480px) {
    .hidden {
      display: none;
    }
  }
  .power {
    animation: fade;
    -webkit-animation: fade 0.3s;
  }
  .lrc {
    padding: 0 20px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    animation: fade;
    -webkit-animation: fade 0.3s;
    .lrc-text {
      margin: 0 8px;
      display: -webkit-box;
      -webkit-box-orient: vertical;
      -webkit-line-clamp: 1;
      overflow: hidden;
      word-break: break-all;
    }
    .i-icon {
      width: 18px;
      height: 18px;
      display: inherit;
    }
  }
}
</style>