<script setup lang="ts">
import Title from "@atoms/title.vue"
import Post from "@molecules/threads.post.vue"
import ImageButton from "@atoms/imageButton.vue"

const props = defineProps({
  emoji: {
    type: String
  },
  username: {
    type: String
  },
  title: {
    type: String
  },
  server: {
    type: String
  },
})
</script>

<template>
  <div class="w-screen text-center flex justify-center mt-12">
    <div class="w-3/5">
      <div class="flex">
        <Title text="Threads" class="text-left" />
        <div class="ml-10">
          <ImageButton src="/icons/ellipsis.circle.fill.svg" size="35" />
        </div>
      </div>
      <div class="mt-3">
        <div class="border-t-2 border-zinc-800">
          <Post :username="username" :emoji="emoji" :title="title" :server="server" />
          <Post :username="username" :emoji="emoji" :title="title" :server="server" />
          <Post :username="username" :emoji="emoji" :title="title" :server="server" />
          <Post :username="username" :emoji="emoji" :title="title" :server="server" />
        </div>
      </div>
    </div>
  </div>
</template>
