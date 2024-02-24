<script setup lang="ts">
const props = defineProps({
  label: {
    type: String
  },
  variant: {
    type: String
  }
})

const emits = defineEmits(["clicked"])

const clicked = () => {
  emits("clicked")
}
</script>

<template>
  <div>
    <div v-if="variant === 'primary'" class="m-3">
      <button class="px-5 py-2 bg-gray-200 text-black font-semibold rounded-full hover:bg-gray-300" @click="clicked">
        {{ props.label }}
      </button>
    </div>
    <div v-if="variant === 'emoji'" class="m-3">
      <button class="px-2 py-1 bg-zinc-800 text-sky-500 font-semibold text-xs rounded hover:bg-neutral-700" @click="clicked">
        {{ props.label }}
      </button>
    </div>
  </div>
</template>
