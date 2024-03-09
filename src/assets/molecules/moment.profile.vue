<script setup lang="ts">
import Button from "@atoms/button.vue"

const props = defineProps<{
  username: string;
  src: string;
  message: string;
  ip: string;
  port: string;
  label: string;
}>()
const emits = defineEmits(["clicked"])

const click = () => {
  emits("clicked")
}
</script>

<template>
  <div class="w-full bg-zinc-900 px-5 py-3 border-zinc-800 border-2 mb-12">
    <div class="flex">
      <img :src="src" class="rounded-full h-10 flex-none mx-2">
      <div class="flex flex-col text-left">
        <p class="text-white font-bold text-xl opacity-80">{{ username }}</p>
        <div class="text-zinc-400 text-base">
          <p>{{ message }}</p>
        </div>
      </div>
    </div>
    <Button :label="label" variant="primary" @clicked="click" />
  </div>
</template>
