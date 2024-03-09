<script setup lang="ts">
import Top from "@organisms/home.top.vue"
import Moment from "@organisms/moment.vue"
import Threads from "@organisms/threads.vue"
import About from "@organisms/about.vue"

//  インターフェースの定義
interface data {
  me: { username: string, usericon: string };
  marquee: string;
  backgroundimage: string;
  Moment: {
    usericon: string;
    username: string;
    message: string;
    uuid: string;
    ip: string;
    port: string;
    replys: [];
  }[];
  Threads: {
    emoji: string;
    username: string;
    title: string;
    server: string;
  }[];
}

const props = defineProps<{
  data: data;
}>()

const clickedMarquee = () => { }

</script>

<template>
  <div>
    <Top :backgroundimage="data.backgroundimage" :marquee="data.marquee" @clickedMarquee="clickedMarquee" />
    <Moment :momentData="data.Moment" :usericon="data.me.usericon" :InputView="true" :MomentView="true" />
    <Threads :threadData="data.Threads" />
    <About />
  </div>
</template>
