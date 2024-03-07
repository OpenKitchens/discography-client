<script setup lang="ts">
import { ref } from "vue"
import pages from "@pages/home.vue"
import axios from "axios"

const data: any = ref({})

axios.get(`http://localhost:3000/api?garlic=getHome`)
  .then((response) => {
    data.value = response.data.data
  })
  .catch((error) => {
    console.error("Error:", error.response.data)
  })


</script>

<template>
  <pages :data="data" />
</template>
