<template>
  <main>
    <div class='bg-gray-200 h-screen'>
      <div class="text-center mb-8 pt-8">
        <h1 class="title-font lg:text-7xl sm:text-5xl text-5xl mb-4 font-bold text-gray-800 mb-4 uppercase">IPTV Reproductor</h1>
        <p class="leading-relaxed font-medium text-lg text-center xl:w-2/4 lg:w-3/4 mx-1 md:mx-auto mb-5">Demo del IPTV en Vue + Nuxt</p>
      </div>
      <div class='flex justify-center'>
        <client-only>
        <VideoPlayer></VideoPlayer>
        </client-only>
      </div>
    </div>
  </main>
</template>

<script>
import VideoPlayer from '~/components/VideoPlayer'

export default {
  components: {
    VideoPlayer
  },
  data() {
    return {
      show: false,
    }
  }
}
</script>
<style>
body {
  @apply bg-gray-200
}
</style>
