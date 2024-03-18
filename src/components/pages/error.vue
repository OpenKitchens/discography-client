<script setup lang="ts">
import Logo from "@atoms/logo.vue"
import Background from "@molecules/background.vue"
</script>

<template>
  <div>
    <Background src="/images/error.png"></Background>
    <div class="w-screen" style="height: 9rem;">
      <div class="w-screen">
        <div class="position absolute ml-32 mt-24 block">
        </div>
      </div>
    </div>

    <div class="w-screen" style="height: 9rem;">
      <div class="w-screen">
        <div class="position absolute ml-32 mt-5 block">
          <Logo />
          <h1 class="text-left font-extrabold tracking-tight text-5xl bg-yellow-400 pb-2">Something to wrong.</h1>
          <p class="text-white text-left text-xl bg-black">クライアントを再起動するか、マイノードを確認してください。</p>
        </div>
      </div>
    </div>
  </div>
</template>