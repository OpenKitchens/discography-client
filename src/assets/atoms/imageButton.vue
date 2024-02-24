<script setup lang="ts">
const props = defineProps({
  src: {
    type: String
  },
  size: {
    type: String
  }
})

const emits = defineEmits(["clicked"])

const clicked = () => {
  emits("clicked")
}
</script>

<template>
  <button class="text-white" @click="clicked">
    <img :src="src" :width="size" class="hover:opacity-80">
  </button>
</template>
