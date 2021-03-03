<template>
    <div v-if="video" class="p-5">
        <div class="ratio ratio-16x9">
            <iframe :src="videoUrl" allowfullscreen />
        </div>
        <div class="details">
           <h4>{{ video.snippet.title }}</h4>
           <p>{{ video.snippet.description }}</p>
        </div>      
    </div>
</template>

<script>
    export default {
        name: 'VideoDetail.vue',
        props: {
            video: Object
        },
        computed: {
            videoUrl() {
                const { videoId } = this.video.id; // taken property name off the end, as same as { variable }
                return `https://www.youtube.com/embed/${videoId}`;  //iterpolated rather than concatenated
            }
        },
    };
</script>

<style scoped>
    .details {
        margin-top: 10px;
        padding: 10px;
        border: 1px solid #ddd;
        border-radius:4px;
    }
</style>