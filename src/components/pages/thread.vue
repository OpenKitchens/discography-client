<script setup lang="ts">
import Title from "@atoms/title.vue"
import Top from "@organisms/thread.top.vue"
import Moment from "@organisms/moment.vue"
import About from "@organisms/about.vue"
import Profile from "@molecules/moment.profile.vue"

//  インターフェースの定義
interface Thread {

  title: string;
  server: {
    uuid: string;
    ip: string;
    port: string;
  },
  replys: []

}
interface data {
  me: { username: string, usericon: string };
  thread: Thread;
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
}

const props = defineProps<{
  data: data;
}>()

console.log(props.data.me)
</script>

<template>
  <div>
    <Top :backgroundimage="data.me.data.backgroundimage" />
    <div class="flex">
      <Moment :momentData="data.thread.replys" :usericon="data.me.data.usericon" :MomentView="false" :InputView="true"
        :threadTitle="data.thread.title">
        <Profile src="" :username="data.server.data.title" :message="data.server.data.about" label="サーバーを追加" />
      </Moment>
    </div>
    <About />
  </div>
</template>