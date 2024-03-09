<script setup lang="ts">
import axios from "axios"
import { ref } from "vue"
import { useRoute } from "vue-router"
import pages from "@pages/thread.vue"
const route = useRoute()

const data = ref()

axios.get(`http://localhost:3000/api?garlic=getThread&ip=${route.query.ip}&port=${route.query.port}&uuid=${route.query.uuid}`)
  .then((response) => {
    data.value = response.data
    console.log(response.data.thread)
  })
  .catch((error) => {
    console.error("Error:", error.response.data)
  })
</script>


<template>
  <pages :data="data" />
</template>