<script setup lang="ts">
import Top from "@organisms/home.top.vue"
import Moment from "@organisms/moment.vue"
import Threads from "@organisms/threads.vue"
import About from "@organisms/about.vue"

//  インターフェースの定義
interface Moment {
  usericon: string;
  username: string;
  message: string;
  uuid: string;
  ip: string;
  port: string;
}

interface Thread {
  emoji: string;
  username: string;
  title: string;
  server: string;
  uuid: string;
  ip: string;
  port: string;
}

interface Data {
  username: string;
  usericon: string;
  backgroundimage: string;
  Moment: Moment[];
  Threads: Thread[];
}

const props = defineProps<{
  data: Data;
}>()


</script>

<template>
  <div>
    <Top :backgroundimage="data.backgroundimage" />
    <Moment :momentData="data.Moment" :usericon="data.usericon" :InputView="true" :MomentView="true" threadTitle="" />
    <Threads :threadData="data.Threads" width="width: 50vw" />
    <About />
  </div>
</template>
