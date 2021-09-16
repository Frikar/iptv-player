<template>
  <main>
    <div class='bg-gray-200 h-screen'>
      <div class="text-center mb-8 pt-8">
        <h1 class="title-font lg:text-7xl sm:text-5xl text-5xl mb-4 font-bold text-gray-800 mb-4 uppercase">IPTV Reproductor</h1>
        <p class="leading-relaxed font-medium text-lg text-justify md:text-center xl:w-2/4 lg:w-3/4 mx-1 md:mx-auto mb-5">Demo del IPTV en Vue + Nuxt</p>
      </div>
      <div class='flex justify-center'>
        <VideoPlayer :options='videoOptions'></VideoPlayer>
      </div>
    </div>
  </main>
</template>

<script>
import videojs from 'video.js'
import VideoPlayer from '~/components/VideoPlayer'

export default {
  components: {
    VideoPlayer
  },
  data() {
    return {
      show: false,
      player: '',
      videoOptions: {
        controls: true,
        sources: [
          {
            src:
              "https://vdo1.streamgato.us:3776/stream/play.m3u8?PlaylistM3UCL",
            type: "application/x-mpegURL"
          }
        ]
      }
    }
  },
  methods: {
    changeChannel(video) {
      this.player = video
      console.log(this.player)
      this.videoOptions.sources[0].src = "https://5975e06a1f292.streamlock.net:4443/sanluistv/ngrp:sanluistv_all/playlist.m3u8?PlaylistM3UCL"
    }
  }
}
</script>
