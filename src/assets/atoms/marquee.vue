<script setup lang="ts">
const props = defineProps({
  label: {
    type: String
  },
});

const emits = defineEmits(["clickedMarquee"]);

const click = () => {
  emits("clickedMarquee");
};
</script>

<template>
  <div class="marquee">
    <div class="marquee-inner">
      <button @click="click">
        {{ label }}
      </button>
    </div>
  </div>
</template>

<style scoped>
/** マーキーさせたい部分 */
.marquee {
  overflow: hidden; /* スクロールバーが出ないように */
  position: relative; /* マーキーの内容部分の位置の基準になるように */
  background-color: black;
  border-top: solid 1px #2e2e2e;
  border-bottom: solid 1px #2e2e2e;
  padding-top: 5px;
  padding-bottom: 5px;
}
/* マーキーの内容部分の高さ確保 */
.marquee::after {
  content: "";
  white-space: nowrap;
  display: inline-block;
}
/* マーキーさせたい部分(内側) */
.marquee > .marquee-inner {
  position: absolute;
  top: 0;
  white-space: nowrap;
  animation-name: marquee;
  animation-timing-function: linear;
  animation-duration: 20s;
  animation-iteration-count: infinite;
}
/* マウスオーバーでマーキーストップ */
.marquee > .marquee-inner:hover {
  animation-play-state: paused;
  cursor: default;
}
/** マーキーアニメーション */
@keyframes marquee {
  0% {
    left: 100%;
    transform: translate(0);
  }
  100% {
    left: 0;
    transform: translate(-100%);
  }
}

button {
  background: none;
  color: white;
  font-size: 15px;
  font-weight: bold;
  border: none;
  outline: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  margin: 0;
  padding-top: 5px;
  padding-bottom: 5px;
}
</style>
