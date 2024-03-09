<script setup lang="ts">
import Header from "@molecules/top.header.vue"
import Background from "@molecules/background.vue"

const props = defineProps({
  backgroundimage: {
    type: String
  },
  threadTitle: {
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
    <div class="w-screen" style="height: 9rem;">
      <div class="w-screen">
        <div class="position absolute ml-32 mt-24 block">
          <h1 class="text-white text-center font-extrabold tracking-tight text-4xl">{{ threadTitle }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>
