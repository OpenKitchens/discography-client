<script setup lang="ts">
import Header from "@molecules/top.header.vue"
import Background from "@molecules/background.vue"
import User from "@molecules/top.user.vue"

const props = defineProps({
  backgroundimage: {
    type: String
  },
  usericon: {
    type: String
  },
  username: {
    type: String
  },
  server: {
    type: String
  }
})


</script>

<template>
  <div>
    <div class="fixed z-30 w-screen">
      <Header />
    </div>
    <Background :src="backgroundimage"></Background>

    <User :username="username" :usericon="usericon" :server="server" />
  </div>
</template>
