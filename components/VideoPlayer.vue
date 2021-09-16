<template>
  <div>
    <video ref='videoPlayer' class='video-js shadow-xl' data-setup='{}' width='400px' height='200px'></video>
    <Button class='bg-green-400' name='Canal 1' url='https://5975e06a1f292.streamlock.net:4443/sanluistv/ngrp:sanluistv_all/playlist.m3u8?PlaylistM3UCL' @change-event='change'></Button>
    <Button class='bg-red-400' name='Canal 2' url='https://593b04c4c5670.streamlock.net:443/8018/8018/playlist.m3u8?PlaylistM3UCL' @change-event='change'></Button>
    <Button class='bg-blue-400' name='Canal 3' url='http://azxtv.com/hls/stream.m3u8?PlaylistM3UCL' @change-event='change'></Button>
  </div>
</template>

<script>
import videojs from 'video.js'
import Button from '~/components/Button'

export default {
  name: 'VideoPlayer',
  components: {
    Button
  },
  data() {
    return {
      player: null,
      videoOptions: {
        autoplay: true,
        controls: true,
        sources: [
          {
            src: 'https://vdo1.streamgato.us:3776/stream/play.m3u8?PlaylistM3UCL',
            type: 'application/x-mpegURL'
          }
        ]
      }
    }
  },
  mounted() {
    this.player = videojs(this.$refs.videoPlayer, this.videoOptions, function onPlayerReady() {
      // eslint-disable-next-line no-console
      console.log('onPlayerReady', this)
    })
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose()
    }
  },
  methods: {
    change(url) {
      this.player.src(url)
    }
  }
}
</script>
