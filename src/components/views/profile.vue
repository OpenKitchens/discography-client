<script setup lang="ts">
import axios from "axios"
import { ref } from "vue"
import { useRoute } from "vue-router"
import pages from "@pages/profile.vue"
import error from "@pages/error.vue"

const route = useRoute()

const data: any = ref({})
data.value.view = false
const errorView = ref(false)

axios.get(`http://localhost:3000/api?garlic=getNetProfile&ip=${route.query.ip}&port=${route.query.port}`)
  .then((response) => {
    data.value = response.data
    console.log(response.data)
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
  <pages :data="data" v-if="data.view"/>
  <error v-if="errorView" />
</template>
