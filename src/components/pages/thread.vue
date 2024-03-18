<script setup lang="ts">
import Title from "@atoms/title.vue"
import Top from "@organisms/thread.top.vue"
import Moment from "@organisms/moment.vue"
import About from "@organisms/about.vue"
import Profile from "@molecules/moment.profile.vue"
import { useRouter } from "vue-router"

const router = useRouter()

interface Server {
  uuid: string;
  ip: string;
  port: string;
  cuuid: string;
}

interface serverView {
  title: string;
  about: string;
}

interface Reply {
  usericon: string;
  username: string;
  message: string;
  uuid: string;
  ip: string;
  port: string;
}

interface Me {
  usericon: string;
  username: string;
  backgroundimage: string;
}

interface ThreadData {
  me: Me;
  title: string;
  server: Server;
  serverView: serverView;
  replys: Reply[];
}


const props = defineProps<{
  data: ThreadData;
}>()

console.log(props.data)

const click = () => {
  console.log(props.data.server)
  router.push({
    name: 'server',
    query: { ip: props.data.server.ip, port: props.data.server.port, uuid: props.data.server.uuid, cuuid: props.data.server.cuuid, index: 0 }
  })
}
</script>

<template>
  <div>
    <Top :backgroundimage="data.me.backgroundimage" />
    <div class="flex">
      <Moment :momentData="data.replys" :usericon="data.me.usericon" :MomentView="false" :InputView="true"
        :threadTitle="'# ' + data.title">
        <Profile src="" :username="data.serverView.title" :message="data.serverView.about" label="サーバービュー" @clicked="click" />
      </Moment>
    </div>
    <About />
  </div>
</template>