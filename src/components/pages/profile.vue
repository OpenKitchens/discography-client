<script setup lang="ts">
import Top from "@organisms/profile.top.vue"
import Moment from "@organisms/moment.vue"
import Threads from "@organisms/threads.vue"
import About from "@organisms/about.vue"

interface MyThread {
  emoji: string;
  username: string;
  title: string;
  server: string;
  uuid: string;
  ip: string;
  port: string;
}

interface MyMoment {
  usericon: string;
  username: string;
  message: string;
  uuid: string;
  ip: string;
  port: string;
}

interface Data {
  username: string;
  usericon: string;
  about: string;
  server: string;
  banner: string;
  myThread: MyThread[];
  myMoment: MyMoment[];
}

// プロパティの型定義
const props = defineProps<{
  data: Data;
}>()
</script>

<template>
  <div>
    <Top :backgroundimage="data.banner" :usericon="data.usericon" :username="data.username"
      :server="data.server" />
    <Moment :momentData="data.myMoment" :InputView="false" :MomentView="true" usericon="" threadTitle="" />
    <Threads :threadData="data.myThread" width="width: 50vw" />
    <About />
  </div>
</template>
