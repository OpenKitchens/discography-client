<script setup lang="ts">
import Input from "@atoms/input.vue"

const props = defineProps({
  label: {
    type: String
  },
  placeholder: {
    type: String
  },
  text: {
    type: String
  },
})

const emits = defineEmits(["clicked"])

const clicked = () => {
  emits("clicked")
}
</script>

<template>
  <div class="w-screen" style="height: 90vh;">
    <div class="h-4/5 w-screen">
      <div style="position: absolute; top: 40%;left: 50%; transform: translate(-50%,-50%)">
        <h1 class="text-white text-center font-extrabold tracking-tight text-4xl">{{ text }}</h1>
        <Input variant="top" :label="label" @clicked="clicked" :placeholder="placeholder" />
      </div>
    </div>
  </div>
</template>
