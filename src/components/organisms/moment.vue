<script setup lang="ts">
import Title from "@atoms/title.vue"
import Form from "@molecules/moment.form.vue"
import Post from "@molecules/moment.post.vue"
import Profile from "@molecules/moment.profile.vue"
import ImageButton from "@atoms/imageButton.vue"
import { ref } from "vue"
import { useRouter } from "vue-router"

const router = useRouter()

interface Moment {
  usericon: string;
  username: string;
  message: string;
  uuid: string;
  ip: string;
  port: string;
}

const props = defineProps<{
  usericon: string;
  momentData: Moment[];
  threadTitle: string;
  InputView: boolean;
  MomentView: boolean;
}>()

const profileView = ref(false)
const profileUserIcon = ref("")
const profileUsername = ref("")
const profileAbout = ref("")
const ip = ref("")
const port = ref("")

const profileOpen = (profileData: any) => {
  profileView.value = true
  profileUserIcon.value = profileData.data.usericon
  profileUsername.value = profileData.data.username
  profileAbout.value = profileData.data.about
  ip.value = profileData.ip
  port.value = profileData.port
}

const click = () => {
  router.push({
    name: 'profile',
    query: { ip: ip.value, port: port.value }
  })
  console.log(ip)
}

</script>

<template>
  <div class="w-screen text-center flex justify-center">
    <div class="w-1/2">
      <h1 class="text-white text-left font-extrabold tracking-tight text-4xl">{{ threadTitle }}</h1>
      <div class="flex" v-if="MomentView">
        <Title text="Moments" class="text-left" />
        <div class="ml-10">
          <ImageButton src="/icons/ellipsis.circle.fill.svg" size="35" />
        </div>
      </div>
      <div class="mt-3">
        <Form placeholder="テキストを入力" :src="usericon" v-if="InputView" class="rounded-t-xl" />
      </div>
      <div v-for="(data, index) in momentData">
        <div>
          <Post :usericon="data.usericon" :username="data.username" :message="data.message" :uuid="data.uuid" :ip="data.ip"
            :port="data.port" @profileOpen="profileOpen" />
        </div>
      </div>
      <div class="w-full bg-zinc-900 px-5 py-3 border-zinc-800 border-x-2 border-b-2">
        <p class="text-black font-semibold text-gray-300">read more</p>
      </div>
    </div>
    <div class="w-1/5 ml-10" v-if="threadTitle || profileView">
      <Title text="Server" class="text-left" v-if="threadTitle" />
      <div class="mt-3 w-full">
        <slot />
      </div>
      <Title text="Profile" class="text-left" v-if="profileView" />
      <div class="mt-3 w-full">
        <Profile :src="profileUserIcon" :username="profileUsername" :message="profileAbout" :ip="ip" :port="port"
          label="アカウントビュー" @clicked="click" v-if="profileView" />
      </div>
    </div>
  </div>
</template>
