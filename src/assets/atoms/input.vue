<script setup lang="ts">
const props = defineProps({
  placeholder: {
    type: String
  },
  variant: {
    type: String
  },
  label: {
    type: String
  }
})

const emits = defineEmits(["clicked"])

const clicked = () => {
  emits("clicked")
}
</script>

<template>
  <div v-if="variant === 'top'" class="mt-10 text-center">
    <input type="text" :placeholder="placeholder" class="rounded-l-lg opacity-70 text-lg px-5 py-2 w-80">
    <button @clicked="clicked" class="rounded-r-lg bg-black text-lg px-5 py-2 text-white hover:opacity-80">{{ label }}</button>
  </div>
  <div v-if="variant === 'primary'" class="text-center">
    <input type="text" :placeholder="placeholder" class="rounded-lg text-lg px-5 py-2 w-full bg-black boder border-zinc-800 border-2 text-white">
  </div>
</template>