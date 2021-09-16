<template>
  <div>
    <video ref="videoPlayer" class="video-js shadow-xl" width="640" height="268" data-setup='{}'></video>
    <button class="flex mx-auto mt-6 text-white bg-indigo-500 border-0 py-2 px-5 focus:outline-none hover:bg-indigo-600 rounded shadow-2xl" @click='change'>Cambiar canal</button>
  </div>
</template>

<script>
import videojs from 'video.js';

export default {
  name: "VideoPlayer",
  data() {
    return {
      player: null,
      videoOptions: {
        autoplay: true,
        controls: true,
        sources: [
          {
            src: "https://vdo1.streamgato.us:3776/stream/play.m3u8?PlaylistM3UCL",
            type: "application/x-mpegURL"
          }
        ]
      }
    }
  },
  mounted() {
    this.player = videojs(this.$refs.videoPlayer, this.videoOptions, function onPlayerReady() {
      // eslint-disable-next-line no-console
      console.log('onPlayerReady', this);
    })
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose()
    }
  },
  methods: {
    change() {
      if (this.player === 'https://5975e06a1f292.streamlock.net:4443/sanluistv/ngrp:sanluistv_all/playlist.m3u8?PlaylistM3UCL') {
        this.player.src("https://vdo1.streamgato.us:3776/stream/play.m3u8?PlaylistM3UCL")
      }
      else {
        this.player.src("https://5975e06a1f292.streamlock.net:4443/sanluistv/ngrp:sanluistv_all/playlist.m3u8?PlaylistM3UCL")
      }
    }
  }
}
</script>
