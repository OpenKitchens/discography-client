<script setup lang="ts">
import Top from "@organisms/profile.top.vue"
import Moment from "@organisms/moment.vue"
import Threads from "@organisms/threads.vue"
import About from "@organisms/about.vue"

// データの型定義
interface Moments {
  usericon: string;
  username: string;
  message: string;
  uuid: string;
  ip: string;
  port: string;
  replys: any[]; // ここは適切な型に置き換える必要があります
}

interface MomentData {
  data: Moments[]
}

interface Threads {
  emoji: string;
  username: string;
  title: string;
  server: string;
}

interface ThreadData {
  data: Threads[]
}

interface UserData {
  data: {
    username: string;
    banner: string;
    usericon: string; // usericonプロパティを追加
    server: string; // usericonプロパティを追加
  };
}

interface Data {
  me: UserData;
  marquee: string;
  backgroundimage: string;
  moment: MomentData;
  thread: ThreadData;
}

// プロパティの型定義
const props = defineProps<{
  data: Data;
}>()
</script>

<template>
  <div>
    <Top :backgroundimage="data.me.data.banner" :usericon="data.me.data.usericon" :username="data.me.data.username"
      :server="data.me.data.server" />
    <Moment :momentData="data.moment.data" :InputView="false" :MomentView="true" />
    <Threads :threadData="data.thread.data" />
    <About />
  </div>
</template>
