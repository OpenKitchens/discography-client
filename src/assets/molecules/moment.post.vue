<script setup lang="ts">
import Button from '@atoms/button.vue';
import ImageButton from '@atoms/imageButton.vue';
const props = defineProps({
  username: {
    type: String
  },
  src: {
    type: String
  },
  message: {
    type: String
  }
})
</script>

<template>
  <div class="w-full bg-zinc-900 px-5 py-3 border-zinc-800 border-x-2 border-b-2">
    <div class="flex">
      <img :src="src" class="rounded-full h-10 flex-none mx-2">
      <div class="flex flex-col text-left">
        <p class="text-white font-bold text-xl opacity-80">{{ username }}</p>
        <div class="text-zinc-400 text-base">
          <p>{{ message }}</p>
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
    <p class="flex"><Button variant="emoji" label="Add emoji" @clicked="" /></p>
  </div>
</template>
