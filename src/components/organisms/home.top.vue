<script setup lang="ts">
import Header from "@molecules/top.header.vue"
import Background from "@molecules/background.vue"
import Broadform from "@molecules/top.broadform.vue"

const props = defineProps({
  backgroundimage: {
    type: String
  },
  marquee: {
    type: String
  }
})

const emits = defineEmits(["clickedMarquee"]);

const clickedMarquee = () => {
  emits("clickedMarquee");
};

</script>

<template>
  <div>
    <div class="fixed z-30 w-screen">
      <Header :marquee="marquee" @clickedMarquee="clickedMarquee" />
    </div>
    <Background :src="backgroundimage"></Background>
    <Broadform text="ディープダイブで見つけよう。" placeholder="アクセスコード" label="追加" @clicked="" />
  </div>
</template>
