<script setup lang="ts">
const props = defineProps({
  text: {
    type: String
  }
})
</script>

<template>
  <div class="">
    <h1 class="text-white font-extrabold tracking-tight text-4xl">{{ text }}</h1>
  </div>
</template>