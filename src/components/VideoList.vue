<template>
        <ul class="list-group px-5">
            <VideoListItem v-for="video in videos"
            :video="video"
            :key="video.etag"
            @videoSelect="onVideoSelect"
            >
            </VideoListItem>
        </ul>
</template>

<script>
    import VideoListItem from "../components/VideoListItem";
    export default {
      name: 'VideoList',
      components: {
          VideoListItem
      },
      props: {
          videos: Array
      },
      methods: {
          onVideoSelect(video) {
              this.$emit('videoSelect', video) // emiting- passing on the video to App component
          }
      } 
    };
</script>

<style scoped>

</style>