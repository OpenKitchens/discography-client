<script setup lang="ts">
import Title from "@atoms/title.vue"
import Post from "@molecules/threads.post.vue"
import ImageButton from "@atoms/imageButton.vue"

interface Threads {
  emoji: string;
  username: string;
  title: string;
  server: string;
  uuid: string;
  ip: string;
  port: string;
};

const props = defineProps<{
  threadData: Threads[];
}>()
</script>

<template>
  <div class="w-screen text-center flex justify-center mt-12">
    <div class="w-1/2">
      <div class="flex">
        <Title text="Threads" class="text-left" />
        <div class="ml-10">
          <ImageButton src="/icons/ellipsis.circle.fill.svg" size="35" />
        </div>
      </div>
      <div class="mt-3">
        <div class="border-t-2 border-zinc-800">
          <div v-for="data in threadData">
            <Post :username="data.username" :emoji="data.emoji" :title="data.title" :server="data.server" :uuid="data.uuid" :ip="data.ip"
            :port="data.port" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
