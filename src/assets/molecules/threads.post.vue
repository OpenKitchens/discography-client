<script setup lang="ts">
import Button from '@atoms/button.vue';
import ImageButton from '@atoms/imageButton.vue';
import { useRouter } from "vue-router"

const router = useRouter()

const props = defineProps({
  username: {
    type: String
  },
  emoji: {
    type: String
  },
  title: {
    type: String
  },
  server: {
    type: String
  },
  ip: {
    type: String
  },
  port: {
    type: String
  },
  uuid: {
    type: String
  }
})

const postClick = () => {
  console.log("postClick")
  console.log(props.uuid)
  console.log(props.ip)

  router.push({
    name: 'thread',
    query: { ip: props.ip, port: props.port, uuid: props.uuid }
  })
}

</script>

<template>
  <div class="w-full bg-zinc-900 px-5 py-3 border-zinc-800 border-b-2" @click="postClick">
    <div class="flex">
      <div class="rounded-full h-20 w-20 flex-none mx-2 py-3 text-5xl bg-zinc-800 p-1 border border-zinc-700">{{ emoji
        }}</div>
      <div class="flex flex-col text-left mt-7 mx-5">
        <p class="text-white font-bold text-xl opacity-80"># {{ title }}</p>
        <div class="text-zinc-400 text-base">
          <p>created by {{ username }}</p>
        </div>
      </div>
      <div class="ml-auto opacity-30 flex mr-7">
        <div class="my-4 mx-2">
          <ImageButton src="/icons/bookmark.svg" @clicked="" />
        </div>
        <div class="my-4 mx-2">
          <ImageButton src="/icons/message.svg" @clicked="" />
        </div>
      </div>
    </div>
    <p class="flex">
    <p class="text-zinc-400 mx-2 my-3">d/ {{ server }}</p><Button variant="emoji" label="Add emoji" /></p>
  </div>
</template>
