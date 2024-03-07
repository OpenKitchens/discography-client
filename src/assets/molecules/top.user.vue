<script setup lang="ts">
const props = defineProps({
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
  <div class="w-screen" style="height: 90vh;">
    <div class="h-4/5 w-screen">
      <div style="position: absolute; top: 40%;left: 50%; transform: translate(-50%,-50%)" class="flex">
        <img :src="usericon" class="rounded-full w-64 border-2">
        <div>
          <p class="text-white font-extrabold tracking-tight text-3xl ml-12 px-5 py-2 bg-black rounded-full inline-block mt-12">{{ server }}</p>
          <h1 class="text-white text-center font-extrabold tracking-tight text-9xl ml-12">{{ username }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>
