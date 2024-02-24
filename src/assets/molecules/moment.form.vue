<script setup lang="ts">
import { ref } from "vue"
import Input from "@atoms/input.vue"
const props = defineProps({
  placeholder: {
    type: String
  },
  src: {
    type: String
  }
})
</script>

<template>
  <div class="flex justify-center w-full bg-zinc-900 px-5 py-3 border border-zinc-800 border-2">
    <img :src="src" class="rounded-full h-10 flex-none mx-2">
    <div class="flex-auto w-5/6 mx-5"><Input variant="primary" :placeholder="placeholder"/></div>
  </div>
</template>
