<script setup lang="ts">
import { useRouter, useRoute } from "vue-router"
import { ref, watch } from 'vue'

const route = useRoute()
const router = useRouter()

const postClick = (ip: string, port: string, cuuid: string, index: number) => {
  router.push({
    name: 'server',
    query: { ip: ip, port: port, cuuid: cuuid, index: index, uuid: route.query.uuid }
  })
}

interface Channel {
  emoji: string;
  title: string;
  ip: string;
  port: string;
  cuuid: string;
}

const props = defineProps<{
  channelData: Channel[];
}>()

console.log(props.channelData)

const queryIndex = ref(parseInt(route.query.index as string)) // route.query.index を数値に変換する

watch(() => route.query, () => {
  queryIndex.value = parseInt(route.query.index as string) // 値が変更されたら再度数値に変換する
})
</script>

<template>
  <div class="w-80 mr-5">
    <div class="w-80" v-for="(channel, index) in channelData">
      <button type="button"
        class="rounded-base text-white text-left font-extrabold tracking-tight text-base px-5 py-2.5 w-80"
        @click="postClick(channel.ip, channel.port, channel.cuuid, index)" v-if="queryIndex != index">
        {{ channel.emoji }} {{ channel.title }}

      </button>
      <button type="button"
        class=" bg-white hover:bg-zinc-300 rounded-base text-left font-extrabold tracking-tight text-base px-5 py-2.5 w-80"
        @click="postClick(channel.ip, channel.port, channel.cuuid, index)" v-if="queryIndex == index">
        {{ channel.emoji }} {{
      channel.title }}

      </button>
    </div>
  </div>
</template>