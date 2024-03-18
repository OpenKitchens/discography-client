<script setup lang="ts">
import Button from '@atoms/button.vue';
import ImageButton from '@atoms/imageButton.vue';
import axios from "axios"
import { ref } from "vue"

interface Reply {
  usericon: string;
  username: string;
  message: string;
}

const props = defineProps<{
  usericon: string;
  username: string;
  message: string;
  uuid: string;
  ip: string;
  port: string;
  replys: Reply[];
}>()

const replys = ref<Reply[]>([]) // 初期値を空の配列に変更
const emits = defineEmits(["profileOpen"])

const postClick = () => {
  console.log("postClick")
  console.log(props.uuid)
  console.log(props.ip)
  console.log(props.port)

  axios.get(`http://localhost:3000/api?garlic=getNetMoment&uuid=${props.uuid}&ip=${props.ip}&port=${props.port}`)
    .then((response) => {
      replys.value = response.data.replys
      console.log(response.data.replys)
      axios.get(`http://localhost:3000/api?garlic=getNetInstantProfile&ip=${props.ip}&port=${props.port}`)
        .then((responseInstant) => {
          console.log(responseInstant)
          emits("profileOpen", { data: responseInstant.data, ip: props.ip, port: props.port })
        }).catch((errorInstant) => {
          console.error("Error:", errorInstant)
        })
    })
    .catch((error) => {
      console.error("Error:", error)
    })
}
</script>


<template>
  <div class="w-full bg-zinc-900 px-5 py-3 border-zinc-800 border-x-2 border-b-2" @click="postClick()">
    <div class="flex">
      <img :src="usericon" class="rounded-full h-10 flex-none mx-2">
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
  <div v-if="replys[0]" class="border-b-2 border-zinc-800 bg-black fadeDown">
    <div v-for="data in replys" class="w-full bg-zinc-900 px-5 py-3 border-zinc-800 border-x-2"
      style="background-color: black;">
      <div class="flex ml-5">
        <img :src="data.usericon" class="rounded-full h-10 flex-none mx-2">
        <div class="flex flex-col text-left">
          <p class="text-white font-bold text-xl opacity-80">{{ data.username }}</p>
          <div class="text-zinc-400 text-base">
            <p>{{ data.message }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.fadeDown {
  animation-name: fadeDownAnime;
  animation-duration: 0.5s;
  animation-fill-mode: forwards;
  opacity: 0;
}

@keyframes fadeDownAnime {
  from {
    opacity: 0;
    transform: translateY(-100px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>