<script setup lang="ts">
import { ref } from "vue"
import pages from "@pages/server.vue"
import error from "@pages/error.vue"
import axios from "axios"
import { useRoute } from "vue-router"
const route = useRoute()

const data: any = ref({})
data.value.view = false
const errorView = ref(false)

axios.get(`http://localhost:3000/api?garlic=getNetServer&ip=${route.query.ip}&port=${route.query.port}&uuid=${route.query.uuid}`)
  .then((response) => {
    console.log(response.data)
    data.value = response.data
    data.value.view = true
    errorView.value = false
  })
  .catch((error) => {
    console.error("Error:", error)
    errorView.value = true
    data.value.view = false
    console.log(errorView.value)
  })
</script>

<template>
  <pages :data="data" v-if="data.view" />
  <error v-if="errorView" />
</template>
