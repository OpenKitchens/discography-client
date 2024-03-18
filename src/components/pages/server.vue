<script setup lang="ts">
import Top from "@organisms/thread.top.vue"
import Threads from "@organisms/threads.vue"
import About from "@organisms/about.vue"
import Channel from "@organisms/server.channel.vue"
import ImageButton from "@atoms/imageButton.vue"
import { useRoute } from "vue-router"

interface Channel {
  emoji: string;
  title: string;
  ip: string;
  port: string;
  cuuid: string;
}

interface Threads {
  emoji: string;
  username: string;
  title: string;
  server: string;
  uuid: string;
  ip: string;
  port: string;
}

interface ServerData {
  title: string;
  about: string;
  channels: Channel[];
  [key: string]: Threads[] | Channel[] | string;
}

const props = defineProps<{
  data: ServerData;
}>()

const route = useRoute()
</script>

<template>
  <div>
    <Top backgroundimage="/images/background.png" />
    <div class="w-screen" style="height: 9rem;">
      <div class="w-screen">
        <div class="position absolute ml-32 mt-5 block">
          <p class="text-white text-left text-xl">{{ data.about }}</p>
          <div class="flex">
            <h1 class="text-white text-left font-extrabold tracking-tight text-5xl">{{ data.title }}</h1>
            <div class="ml-10">
              <ImageButton src="/icons/ellipsis.circle.fill.svg" size="35" />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="flex">
      <Threads :threadData="data[route.query.cuuid as string] as Threads[]" width="width: calc(24rem + 50%)">
        <Channel :channelData="data.channels" />
      </Threads>
    </div>
    <About />
  </div>
</template>