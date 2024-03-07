<script setup lang="ts">
import Button from "@atoms/button.vue"
import { useRouter } from "vue-router"

const router = useRouter()

const props = defineProps<{
  username: string;
  src: string;
  message: string;
  ip: string;
  port: string;
}>()

const click = () => {
  router.push({
    name: 'profile',
    query: { ip: props.ip, port: props.port }
  })
  console.log(props.ip)
}
</script>

<template>
  <div class="w-full bg-zinc-900 px-5 py-3 border-zinc-800 border-2">
    <div class="flex">
      <img :src="src" class="rounded-full h-10 flex-none mx-2">
      <div class="flex flex-col text-left">
        <p class="text-white font-bold text-xl opacity-80">{{ username }}</p>
        <div class="text-zinc-400 text-base">
          <p>{{ message }}</p>
        </div>
      </div>
    </div>
    <Button label="アカウントビュー" variant="primary" @clicked="click" />
  </div>
</template>
