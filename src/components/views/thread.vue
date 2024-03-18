<script setup lang="ts">
import axios from "axios"
import { ref } from "vue"
import { useRoute } from "vue-router"
import pages from "@pages/thread.vue"
import error from "@pages/error.vue"
const route = useRoute()

const data: any = ref({})
data.value.view = false
const errorView = ref(false)

axios.get(`http://localhost:3000/api?garlic=getNetThread&ip=${route.query.ip}&port=${route.query.port}&uuid=${route.query.uuid}`)
  .then((response) => {
    data.value = response.data
    console.log(response.data)
    axios.get(`http://localhost:3000/api?garlic=getNetInstantMe`)
      .then((responseInstant) => {
        data.value.me = responseInstant.data
        console.log(data.value.me)
        axios.get(`http://localhost:3000/api?garlic=getNetInstantServer&ip=${data.value.server.ip}&port=${data.value.server.port}&uuid=${data.value.server.uuid}`)
          .then((responseInstantServer) => {
            data.value.serverView = responseInstantServer.data
            data.value.view = true
            errorView.value = false
          }).catch((errorInstant) => {
            console.error("Error:", errorInstant)
            errorView.value = true
            data.value.view = false
            console.log(errorView.value)
          })

      }).catch((errorInstant) => {
        console.error("Error:", errorInstant)
        errorView.value = true
        data.value.view = false
        console.log(errorView.value)
      })
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