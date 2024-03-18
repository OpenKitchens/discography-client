<script setup lang="ts">
import { ref } from "vue"
const props = defineProps({
  src: {
    type: String
  },
})

const background = ref()
background.value = `background-image: url('${props.src}')`
</script>

<template>
  <div class="h-screen w-screen fixed -z-50">
    <div :style="background" class="h-4/5 w-screen absolute bg-center bg-cover opacity-70"></div>
    <div class="flex items-center justify-center absolute z-10 w-screen h-4/5"></div>
  </div>
</template>
