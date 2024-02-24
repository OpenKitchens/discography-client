<script setup lang="ts">
import Title from "@atoms/title.vue"
import Form from "@molecules/moment.form.vue"
import Post from "@molecules/moment.post.vue"
import ImageButton from "@atoms/imageButton.vue"

const props = defineProps({
  usericon: {
    type: String
  },
  username: {
    type: String
  }
})
</script>

<template>
  <div class="w-screen text-center flex justify-center">
    <div class="w-3/5">
      <div class="flex">
        <Title text="Moments" class="text-left" />
        <div class="ml-10">
          <ImageButton src="/icons/ellipsis.circle.fill.svg" size="35" />
        </div>
      </div>
      <div class="mt-3">
        <Form placeholder="テキストを入力" :src="usericon" />
      </div>
      <Post :src="usericon" :username="username" message="Is this big enough for you?" />
      <Post :src="usericon" :username="username" message="Is this big enough for you?" />
      <Post :src="usericon" :username="username" message="Is this big enough for you?" />
      <Post :src="usericon" :username="username" message="Is this big enough for you?" />
      <Post :src="usericon" :username="username" message="Is this big enough for you?" />
      <Post :src="usericon" :username="username" message="Is this big enough for you?" />
      <Post :src="usericon" :username="username" message="Is this big enough for you?" />
      <div class="w-full bg-zinc-900 px-5 py-3 border-zinc-800 border-x-2 border-b-2">
        <p class="text-black font-semibold text-gray-300">read more</p>
      </div>
    </div>
  </div>
</template>
