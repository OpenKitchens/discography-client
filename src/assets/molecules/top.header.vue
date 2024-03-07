<script setup lang="ts">
import Marquee from "@atoms/marquee.vue"
import Button from "@atoms/button.vue"
import Logo from "@atoms/logo.vue"
import ImageButton from "@atoms/imageButton.vue"
import { RouterLink } from "vue-router"

const emits = defineEmits(["clickedMarquee"]);

const clickedMarquee = () => {
  emits("clickedMarquee");
};

const props = defineProps({
  marquee: {
    type: String
  }
})
</script>

<template>
  <!--<Marquee :label="marquee" @clickedMarquee="clickedMarquee" />-->
  <div class="px-20 flex justify-between px-10" style="-webkit-backdrop-filter: blur(12px);backdrop-filter: blur(12px);">
    <RouterLink to="/"><Logo /></RouterLink>

    <div class="flex">
      <div class="flex pt-3">
        <div class="m-3">
          <ImageButton src="/icons/bookmark.svg" @clicked="" />
        </div>
        <div class="m-3">
          <ImageButton src="/icons/message.svg" @clicked="" />
        </div>
        <div class="m-3">
          <ImageButton src="/icons/search.svg" @clicked="" />
        </div>
      </div>
      <Button label="スレッド投稿" variant="primary" @clicked="" />
    </div>
  </div>
</template>
