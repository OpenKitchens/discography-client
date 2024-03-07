<script setup lang="ts">
import Top from "@organisms/profile.top.vue"
import Moment from "@organisms/moment.vue"
import Threads from "@organisms/threads.vue"
import About from "@organisms/about.vue"

// データの型定義
interface MomentData {
  usericon: string;
  username: string;
  message: string;
  uuid: string;
  ip: string;
  port: string;
  replys: any[]; // ここは適切な型に置き換える必要があります
}

interface ThreadData {
  emoji: string;
  username: string;
  title: string;
  server: string;
}

interface UserData {
  username: string;
  usericon: string;
  data: {
    banner: string;
  };
}

interface Data {
  me: UserData;
  marquee: string;
  backgroundimage: string;
  moment: MomentData[];
  Threads: ThreadData[];
}

// プロパティの型定義
const props = defineProps<{
  data: Data;
}>()
</script>

<template>
  <div>
    <Top :backgroundimage="data.me.data.banner" :usericon="data.me.data.usericon" :username="data.me.data.username" :server="data.me.data.server" />
    <Moment :momentData="data.moment.data" :InputView="false" />
    <Threads :threadData="data.thread.data" />
    <About />
  </div>
</template>
