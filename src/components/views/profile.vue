<script setup lang="ts">
import axios from "axios"
import { ref } from "vue"
import { useRoute } from "vue-router"
import pages from "@pages/profile.vue"
const route = useRoute()

const data = ref()

axios.get(`http://localhost:3000/api?garlic=getProfile&ip=${route.query.ip}&port=${route.query.port}`)
  .then((response) => {
    data.value = response.data
    console.log(response.data)
  })
  .catch((error) => {
    console.error("Error:", error.response.data)
  })
</script>

<template>
  <pages :data="data" />
</template>
