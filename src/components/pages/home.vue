<script setup lang="ts">
import Top from "@organisms/top.vue"
import Moment from "@organisms/moment.vue"
import Threads from "@organisms/threads.vue"
import About from "@organisms/about.vue"

const props = defineProps({
  src: {
    type: String
  },
  usericon: {
    type: String
  },
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
  marquee: {
    type: String
  }
})

const clickedMarquee = () => {
  
}
</script>

<template>
  <div>
    <Top :src="src" :marquee="marquee" @clickedMarquee="clickedMarquee" />
    <Moment :usericon="usericon" :username="username" />
    <Threads :username="username" :emoji="emoji" :title="title" :server="server" />
    <About />
  </div>
</template>
